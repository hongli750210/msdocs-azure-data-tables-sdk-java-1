# azure-data-tables sample application

This is the sample project for using the [azure-data-tables client library](https://search.maven.org/artifact/com.azure/azure-data-tables) with the Azure Cosmos DB Table API.  The quickstart for this application is located at [https://docs.microsoft.com/azure/cosmos-db/table/create-table-java](https://docs.microsoft.com/azure/cosmos-db/table/create-table-java).

## Features

This project demonstrates how to access the Cosmos DB Table API from a Java application using the `azure-data-tables` package in the Azure SDK. The Cosmos DB Table API is a schemaless NoSQL data store used to store tabular data. Each row in an Azure Cosmos DB table has a partition key and row key which together form a unique key for the row. All other properties (columns) of the row are dynamically added when objects are stored in the table. In this way, there is no need to specify the properties (columns) of a table ahead of time as they are automatically added as needed. If an object is loaded to the table that has new properties, the corresponding properties on the table will created automatically.

This sample application is based around storing weather data. A base set of properties (temperature, humidity, pressure, wind direction, and wind speed) are stored for each observation and loaded to a table. However, the GUI can be used to create and store weather observations with additional properties (cloud cover, UV index, air quality index, etc.) to demonstrate how the Table API automatically adds properties to a table as needed. The ability to automatically extend a table in this way is useful for any application where the data sent to the application may dynamically change at any time.

## Getting Started

### Prerequisites

- An [Azure account](https://docs.microsoft.com/dotnet/azure/create-azure-account)
- [Java Development Kit (JDK)](https://docs.microsoft.com/java/azure/jdk/?view=azure-java-stable) with version 8 or above
- [Maven](https://maven.apache.org/)
- [VS Code](https://code.visualstudio.com/) or [IntelliJ IDEA](https://www.jetbrains.com/idea/) 

### Quickstart

This repository contains three subdirectories.
- *starter app* - A starter version of the application without any Azure code. Intended to be used when following the Quickstart at [https://docs.microsoft.com/azure/cosmos-db/table/create-table-java](https://docs.microsoft.com/azure/cosmos-db/table/create-table-java).
- *completed app* - A completed version of the app for those who want to see the finished code or debug through a fully working application.
- *scripts* - Azure CLI and Azure PowerShell scripts to create the Azure resources needed to run this sample.

The fastest way to get started is to run the completed application. For the application to work, you still need provision the appropriate Azure resources and use the appropriate connection string in the sample application.

1. Clone or download the sample application from https://github.com/Azure-Samples/msdocs-azure-data-tables-sdk-java.git
2. Use either the Azure CLI or Azure PowerShell script in the scripts directory to create the appropriate Azure resources. If you do not have Azure CLI or Azure PowerShell installed, you may run either of these scripts in the [Azure Cloud Shell](https://shell.azure.com).
3. Each script will return the appropriate connection string for the sample application to use. Switch to folder `2-completed-app`. Then, add the value of the `connection string` in `pom.xml` file.
```
<profiles>
    <profile>
        <id>local</id>
	<properties>
	    <azure.tables.connection.string>
	        <![CDATA[YOUR-TABLE-SERVICE-CONNECTION-STRING]]>
	    </azure.tables.connection.string>
            <azure.tables.tableName>WeatherData</azure.tables.tableName>
        </properties>
        <activation>
	    <activeByDefault>true</activeByDefault>
	</activation>
    </profile>
</profiles>
```
4. Run the application by executing the method `TablesServiceApplication.main`, and view the result of sample application on web browser by opening the url: [http://localhost:8080](http://localhost:8080).

## Resources

- [azure-data-tables Reference Documentation](https://docs.microsoft.com/java/api/overview/azure/data-tables-readme?view=azure-java-stable)
