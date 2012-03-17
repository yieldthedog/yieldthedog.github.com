---
layout: post
title: "C# code gems #2 - Abstractions via Strings"
date: 2012-03-17 10:06
comments: true
categories: code-gems
published: false;
---

In .NET we have the concept of connection strings which are some weird non consistent bunch of key value pairs, with colons mixed in highly dependent of the DB driver used. To get an overview how such connection strings may look like head over to [Connection Strings.com](http://connectionstrings.com).

For example a MS SQL Server 2008 connection string looks somehow like this

    Data Source=myServerAddress;Initial Catalog=myDataBase;User Id=myUsername;Password=myPassword;

A MySQL connection string may be similar to this

    Server=myServerAddress;Database=myDataBase;Uid=myUsername;Pwd=myPassword;

So constructing a connection string is somehow a pain (thank you so much dear "Connection Strings.com") but there's a class that eases connection string creation in code for MS SQL Server, it's "SqlConnectionStringBuilder".

Let's look at a piece of code to construct a connection string similar to the MS SQL Server 2008 connection string given above.

{% codeblock lang:csharp %}
var builder = new SqlConnectionStringBuilder
        {
            DataSource = "myServerAddress",
            InitialCatalog = "myDataBase",
            UserID = "myUsername",
            Password = "myPassword"
        };

var conn = new SqlConnection(builder.ToString());
{% endcodeblock %} 

So what builder does is to create a string that is then parsed by SqlConnection to connect to the DB. Does this abstract anything? Not really because you have to know what builder to use with what Connection class. With what interface do these classes communicate? The good old string :)

Do I have a better idea to model this? No not really...
