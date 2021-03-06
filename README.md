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

I want to link the Github repository to the Azure WebApp now, so let's do that (outside the venv, in the folder WebApp)

	az webapp up --sku S1 -n AS-Web -g AuswaertsSpiel -l SwitzerlandNorth

This gave me the URL of the webapp. Going there, it prompts to set up deployment. I selected continuous deployment. I selected Github, and then Azure pipelines.

For the logging, I had to add a storage account auswaertsspielweb. I also created a logs container to put the logs in.


