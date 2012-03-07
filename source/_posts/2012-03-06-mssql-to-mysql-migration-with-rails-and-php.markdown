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

    ------IDEAS-----
    MySql Migration Toolkit
    ODBC Export
    ------TODOS-----
    - link tools & solutions
    ----------------

###Mysql Migration Toolkit

The MySql Migration Toolkit look promising at first. You can use a comfortable GUI to select what you want to migrate. The first problems arose, when the toolkit tried to migrate the schema. Obviously my MSSql schema was not compatible with MySql, I found no way to manually correct this errors, so this was a dead end. I looked to me that the work on this tool has stopped, so maybe that's a reason it failed.


###MySql ODBC Connector



##What worked

    ------IDEAS-----
    Rails Schema dump + load
    PHP to connect to mssql and mysql and transfer data
    ------IDEAS-----


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
