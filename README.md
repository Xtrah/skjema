# Kvittering (as a function)

A docker image that runs in [OpenFaaS](https://www.openfaas.com/)

Running on https://kvittering.abakus.no (Note: only available from NTNU/eduroam)

### Getting started

This is one docker image that serves both the python api, and the next/react frontend, this is done by building the webapp as a static site, and serving it as static files through flask.

To run just the frontend:
* Install all packages with `yarn`
* Start the server with `yarn dev`
* Export the static files with `yarn build && yarn export`

To run the backend/everything:
* Make a virtual env with `python -m venv venv`
* Enter the env with `source venv/bin/activate`
* Install packages with `pip install -r kaaf/req.txt`
* Start the server with `python kaaf/server.py`
* If the frontend is exported, the webapp will be available at localhost:5000
* To actually send the generated PDF's, you need to set the `MAIL_ADDRESS` and `MAIL_PASSWORD` env variables

### Generating PDFs

It might be nice to be able to quickly generate PDFs when developing, without having to start up everything. To do this you can run:

```
python kaaf/generate-example.py signature.png output.pdf image0.png image1.png ...
```

Where `signature.png` and `imageN.png` are paths to image files (the latter images are optional)

### Deployment

New versions are automatically built and deployed when pushing to the `prod` branch. Use `faas-cli` if you want to deploy manually.
