# POST requests to JSON data sources in Denodo

The purpose of this repo is to demonstrate the use of Denodo's ability to perform a POST request to an API using SQL, which is a relatively undocumented feature.

> Denodo standard and well documented features include turning JSON data from an API into flattened views, as well as doing INSERT commands to JDBC databases.

## Requirements

* [Denodo Express](https://community.denodo.com/express/download)
* Python installed (covered in step 1)

## Instructions

Follow the below steps to explore this feature:

1. First, create a flask webapp using [these](https://scotch.io/bar-talk/processing-incoming-request-data-in-flask) intructions. The `app.py` file in this repo is based on those intructions, but it is worth following that tutorial first to understand the mechanics of flask.
	* Start the app using `python app.py`

1. Now notice the `app2.py` file in this repo which has been modified to return JSON format from the POST request, see [JSONIFY](https://stackoverflow.com/questions/13081532/return-json-response-from-flask-view) details. The JSONIFY is necessary to ensure that the API returns whatever is posted to it in JSON format, which Denodo is able to turn into a virtual view.
	* Stop the other `app.py` and start the new one using `python app2.py`

1. Now to virtualize in Denodo. The .VQL file contained in this repo contain all the details, and the VQL folder can be virtualized into Denodo.
	1. Install Denodo Express and launch the server and VDP Admin Tool
	2. Import the `flask_post_api.vql` into Denodo using the Denodo IMPORT functionality.
	3. Notice that a data source, base view and flattened view is imported
	4. Open the VQL Shell

1. We can now run queries against our flatted view in Denodo, such as the following, which will execute a POST against the API, and return the results, which can be joined to other applicable views:

`select * from f_post_api_test where lang  = 'TEST'` 


## Notes



