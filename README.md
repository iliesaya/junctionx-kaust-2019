[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/davidrpugh/junctionx-kaust-2019/master?filepath=notebooks%2Fpredicting-solar-power-at-neom.ipynb)

# python-gpu-data-science-project

Repository containing scaffolding for a Python 3-based data science project with GPU acceleration. 
Project organization is based on ideas from [_Good Enough Practices for Scientific Computing_](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510).

## Creating a new project from this template

Simply follow the [instructions](https://help.github.com/en/articles/creating-a-repository-from-a-template) to create a new project repository from this template.

## Project organization

1. Put each project in its own directory, which is named after the project.
2. Put external scripts or compiled programs in the `bin` directory.
3. Put raw data and metadata in a `data` directory.
4. Put text documents associated with the project in the `doc` directory.
5. Put all Docker related files in the `docker` directory.
6. Install the Conda environment into an `env` directory. 
7. Put all notebooks in the `notebooks` directory.
8. Put files generated during cleanup and analysis in a `results` directory.
9. Put project source code in the `src` directory.
10. Name all files to reflect their content or function.

## Conda environments

### Creating the Conda environment

After adding any necessary dependencies to the Conda `environment.yml` file you can create the 
environment in a sub-directory of your project directory by running the following command.

```bash
$ conda env create --prefix ./env --file environment.yml
```

Once the new environment has been created you can activate the environment with the following 
command.

```bash
$ conda activate ./env
```

Note that the `env` directory is *not* under version control as it can always be re-created from 
the `environment.yml` file as necessary.

### Updating the Conda environment

If you add (remove) dependencies to (from) the `environment.yml` file after the environment has 
already been created, then you can update the environment with the following command.

```bash
$ conda env update --prefix ./env --file environment.yml --prune
```

## Using Docker

In order to build Docker images for your project and run containers with GPU acceleration you will 
need to install 
[Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/), 
[Docker Compose](https://docs.docker.com/compose/install/) and the 
[NVIDIA Docker runtime](https://github.com/NVIDIA/nvidia-docker).

Detailed instructions for using Docker to build and image and launch containers can be found in 
the `docker/README.md`.



Predicting the Future of Solar Power Generation at NEOM
Solar power generation forecasts will be a critical need if SOs are to balance NEOM's grid. We built an ML model to forecast solar power generation that takes into account NEOM's weather patterns.

Inspiration
Solar power generation forecasts will be a critical need if SOs are to balance NEOM's smart electricity grid with nearly 100% renewables. Even though NEOM is blessed with plenty of solar radiation, NEOM also experiences substantial fluctuations in temperature, wind, and dust and these factors can all have a substantial impact on solar power generation. We built an ML model capable of accurately forecasting solar power generation that takes into account NEOM's unique weather patterns and created a few prototype interactive dashboards to display the data.

What it does
Our model uses ML techniques to predict future solar power generation at NEOM as a function of the weather data as well as the history solar power generation. After training our model on historical data, we can generate a new forecast for next day's solar power generation. Once the next day's actual values of solar power generation are observed, our model can be automatically re-trained and improved. Model can easily be retrained with weekly or monthly forecast horizons if longer forecasts are required by the SO.

Our interactive dashboard allows the user to interrogate the historical weather and solar power generation data for NEOM as well as to display forecasts of future solar power generation. Dashboard can generate user notifications via the Telegram mobile app to indicate significantly changes to either weather or solar energy forecasts.

Our web and mobile app prototype will allow users (SOs, residential, and industrial prosumers) at NEOM to interact with weather and solar energy forecasts and to receive alerts about significant upcoming changes to either.

How we built it
We built the ML model using widely used open-source tools: Python, Jupyter, Scikit-learn, Keras, and Tensorflow. Our interactive dashboard leveraged another open-source tool called Grafana. We used Adobe XD to prototype our web and mobile apps.

Challenges we ran into
Finding the right machine learning approach. We evaluated a number of classical ML approaches including linear regression, multi-task elasticnet, multi-task lass regression, random forest regression, and GRU and LSTM deep neural networks. Random forest regression eventually emerged as the most performant.

Finding the right dashboard tool. We attempted to roll our own but then decided this approach was too time consuming and explored a few off-the-shelf dashboard solutions before eventually settling on Grafana.

Injecting the ML model into a web application turned out to be significantly more difficult than we had suspected.

Accomplishments that we're proud of
Our overall concept was very solid and useful.
Our interactive dashboard with mobile notifications is really cool!
Our ML modeling pipeline with good forecasting results could be put into production at NEOM.
What we learned
New machine learning approached and data analysis techniques.
Serving machine learning models in web and mobile apps is hard!
Teamwork!
What's next for Forecasting Solar Power Generation for NEOM using ML?
Predicting the future or electricity demand at NEOM!
