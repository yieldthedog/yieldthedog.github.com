---
layout: post
title: "MSSql to MySql migration with a little help of Rails and PHP"
date: 2012-03-06 21.28
published: false
comments: true
categories:
  - mssql
  - mysql
  - migration
  - rails
  - php
---

##The problem
    
You want to migrate a MSSql database to MySql. You have rather large schema and don't want to do it by hand.


##Possible solutions

###Mysql Migration Toolkit

The [MySql Migration Toolkit](http://dev.mysql.com/doc/migration-toolkit/en/:) look promising at first. You can use a comfortable GUI to select what you want to migrate. The first problems arose, when the toolkit tried to migrate the schema. Obviously my MSSql schema was not compatible with MySql, I found no way to manually correct this errors, so this was a dead end. I looked to me that the work on this tool has stopped, so maybe that's a reason it failed.


###MySql ODBC Connector

When you install the [ODBC Connector](http://dev.mysql.com/downloads/connector/odbc/) for MySql, theory claims, that you can select it from the SQL Management Studio to export data to it. However, reality looked a bit different, when I tried it, there was no MySql entry. Bad luck.

##What worked

After 6 hours of trail and error and no success with any tools, I gave up.

As the project was in Railsd, I used `rake db:schema:dump` to get the schema definition from the MSSql server in Ruby code. Afterwards I changed the connection to the MySql server and tried `rake db:schema:load`. As expected I had no luck, but with the big difference, that now I had some code that I could mangle and massage.

There were only problems that were solved in mere seconds:

  - an index on varchar(9999)
  - unsupported type, where another one could be used
  - ...

So now I had my schema ready in MySql waiting for some data. As I'm a long time PHP programmer, too, I knew that PHP lets you easily connect to MySql and MSSql with nearly the same patterns. So I gave it a try and came up with this console script:

{% codeblock lang:ruby %}
<?php

#Connection variables :
$mysql_host = '';
$mysql_user = '';
$mysql_password = '';
$mysql_database = '';
$mysql_link = mysql_connect(
  $mysql_host,
  $mysql_user,
  $mysql_password);

$mssql_host = '';
$mssql_user = '';
$mssql_password = '';
$mssql_database = '';
$mssql_link = mssql_connect(
  $mssql_host,
  $mssql_user, 
  $mssql_password);

$tables = array(/* LIST THE TABLES YOU WANT TO MIGRATE HERE */);

#Select the databases:
mysql_select_db($mysql_database);
mssql_select_db($mssql_database);

#Migrate the data:
foreach($tables as $table){

	$m_res = mssql_query('select * from '. $table);

	$j = 0;

	while($rec = mssql_fetch_array($m_res, MSSQL_NUM)){
		echo $table, ' >> ', $j++, "\n";
		$cols = count($rec);
		for($i = 0; $i < $cols; $i++){
			if(is_string($rec[$i])){
				$rec[$i] = "'" . mysql_real_escape_string($rec[$i]) . "'";
			}
			if(is_null($rec[$i])) $rec[$i] = 'NULL';
		}

		$query = 'insert into '.$table." values (" . implode(",", $rec) . ");";
		$res = mysql_query($query);
		if(!$res) echo $query, ' >>>>>>>>> ', mysql_error(), "\n";
	}

}

{% endcodeblock %}

Probably this is not the most performant way to migrate, simply due to the fact that there are no batch inserts, but it let me easily see the errors and the progress I was making. The whole process - all errors included - took me less time and energy, that I wasted on research. Being a programmer I normally favor coding over tools. Sometimes the effort isn't worth it, this time it was.

I believe that my approach should work on any project and is not bound to MySql and MSSql. The boundaries are the possible database connectors that are available for PHP and Ruby (Rails).
