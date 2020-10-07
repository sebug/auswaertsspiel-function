# Auswärtsspiel-Function
Small proof of concept of an Azure Function with Python and the corresponding
pipelines.

To start, let's create the resources in Azure

	az group create -n AuswaertsSpiel -l SwitzerlandNorth
	az appservice plan create -g AuswaertsSpiel -n ASPlan --sku S1
	az webapp create -g AuswaertsSpiel -p ASPlan -n AS-Web
	az webapp create -g AuswaertsSpiel -p ASPlan -n AS-API


The web app we're going to do as a standard Flask app:

	python3 -m venv WebApp
	source WebApp/bin/activate
	pip install Flask
	export FLASK_APP=app.py
	bin/flask run


