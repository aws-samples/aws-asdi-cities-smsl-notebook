# Investigating environmental characteristics of US cities using publicly available ASDI datasets
The "Work From Home" trend has forever changed how employees view their careers and their work environment. As countries reopened and COVID-19 restrictions were relaxed, the "Great Resignation" started and interest in remote work and flexible-hours roles skyrocketed. Employees can now earn a higher salary in a low cost of living area, travel whilst working, live closer to friends and family and save time and money from the daily office commute.

An environmentally sustainable lifestyle and a "Digital Nomad" career certainly sounds appealing and achievable in theory. 

However, there are many socio-economic and environmental considerations for choosing where to live and work so it is worth doing a lot of research (and crunching the data!) before committing to this life-changing decision.

In this notebook, I'll gather insights from the following ASDI datasets: \
1. [Air quality data from OpenAQ](https://registry.opendata.aws/openaq/) \
2. [Climate data from NOAA U.S. Climate Normals](https://registry.opendata.aws/noaa-climate-normals/) \
3. [Population data from CIESIN and Meta](https://registry.opendata.aws/dataforgood-fb-hrsl/) \
4. [Built environment information from Open City Model](https://registry.opendata.aws/opencitymodel/) \

Since this demo project is presented at the re:MARS 2022 conference, I'll characterise Las Vegas, Nevada from these datasets. Please feel free to adapt the code to your own cities of interest.

This Jupyter notebook uses AWS SageMaker Studio Lab and Python 3.8 and can be run for free using Amazon SageMaker Studio Lab and open-source Amazon Sustainability Data Initiative (ASDI) datasets without needing an AWS account.

Thank you to Damon Cortesi for his [code example](https://dacort.dev/posts/emr-eks-custom-images-with-openaq/#mapping-coordinates-to-counties).

<hr>

## AWS SageMaker Studio Lab
You can sign up for SageMaker Studio Lab and use it for free without an AWS account. You can select between a CPU or GPU compute each time you start your project runtime. CPU runtime is limited to 12 hours per session. GPU runtime is limited to 4 hours per session. After your session ends, you can log back in for another session. Your data and notebooks are persisted. 

After clicking the launch button below, select `Clone Entire Repo`, ensuring that `Search for environment.yml and build Conda environment` is chosen, and select `OK` to the `Confirm you want to build Conda environment` pop up message when prompted.

When it's done installing and configuring the conda environment, open the "ASDI_Cities_Demo.ipynb" notebook file.  Click-Enter to run each row and wait a moment to see the results of each line before proceeding to the next. The line marker should change to a number when it's successfully run that line, i.e. "[5]" means that it has run line 5.

<a href="https://studiolab.sagemaker.aws/import/github/https://github.com/aws-samples/aws-asdi-cities-smsl-notebook/blob/main/ASDI_Cities_Demo.ipynb" rel="nofollow"><img src="https://camo.githubusercontent.com/8c5378ff3bf6f71a57442940234293bd63c7ed2418d64f74f2bda3dc6f2904ed/68747470733a2f2f73747564696f6c61622e736167656d616b65722e6177732f73747564696f6c61622e737667" alt="Open In SageMaker Studio Lab" data-canonical-src="https://studiolab.sagemaker.aws/studiolab.svg" style="max-width: 100%;"></a></p>


## Dataset download instructions for use in the Jupyter notebook
The Jupyter notebook uses datasets from multiple sources, including the Amazon Sustainability Data Initiative. Detailed instructions are provided within the code cells on how to download the datasets from the provided URLs and upload the files to the correct directory within SageMaker Studio Lab. The [JupyterLab documentation](https://jupyterlab.readthedocs.io/en/stable/user/files.html#uploading-and-downloading) provides instructions on uploading files.

The code repo uses the following directories to store each data source:\
```
aws-asdi-cities-smsl-notebook
|── `Data1_NV_State`               <- Datasets from Clark County GIS Management Office and ArcGIS Hub
|── `Data2_ASDI1_OpenAQ`           <- Datasets from OpenAQ API 
|── `Data3_ASDI2_NOAA_US`          <- Datasets from s3://noaa-normals-pds/
|── `Data4_ASDI3_CIESIN_Meta`      <- Datasets from s3://datafordgood-fb-data/demographic_csvs/
|── `Data5_ASDI4_OpenCityModel`    <- Datasets from s3://opencitymodel/2019-jun/
|── ASDI_Cities_Demo.ipynb         <- Jupyter notebook performing analyses on datasets
|── CODE_OF_CONDUCT.md
|── CONTRIBUTING.md
|── environment.yml                <- Environment file for installing Python libraries in conda
|── LICENSE
|── README.md
```

For example, `Data1_NV_State/Clark_County_Place_Political_Boundaries.zip` is a shapefile in ZIP format downloaded from [Place dataset](https://clarkcountygis-ccgismo.hub.arcgis.com/datasets/ccgismo::place/explore?location=35.922613%2C-114.964700%2C9.85) from the Clark County GIS Management Office and uploaded into the `Data1_NV_State` directory. 

<br>

**Clark County GIS Management Office:** https://clarkcountygis-ccgismo.hub.arcgis.com/search?collection=Dataset \
**ASDI Homepage:** https://sustainability.aboutamazon.com/environment/the-cloud/asdi \
**ASDI datasets:** https://registry.opendata.aws/collab/asdi/ \
**OpenAQ:** https://registry.opendata.aws/openaq/ \
**NOAA U.S. Climate Normals:** https://registry.opendata.aws/noaa-climate-normals/ \
**CIESIN and Meta:** https://registry.opendata.aws/dataforgood-fb-hrsl/ \
**Open City Model:** https://registry.opendata.aws/opencitymodel/ \


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.