# Recommendation-system-social-network
Recommendation-system-social-network
It is necessary to implement a recommendation system for posts on a social network, which will return posts for each user at any time that will be shown to the user in his social network feed.

  Initial data:
  • As basic raw data - table with PostreSQL
  • Users - user data
  • Posts - post data
  • Feeds - user activity data
  • The set of users is fixed and no new ones will appear*
  • Models are not retrained when using services*

Uploaded to the repository:

Download data and EDA.ipynb - Loading data from the database to the Jupyter Hub, reviewing the data
Create features.ipynb - Creation of features and training sample
Train model .ipynb - Training models and assessing their quality on the validation set.
Test service.ipynb - Imitation of a printer on the jupyter notebook
FastAPI service - The service downloads data from PostgreSQL, loads the model and, based on a get request, issues recommendations to each user in JSON format
Conceptual diagram of working with data



Main libraries used
PANDAS NUMPY fastapi sqlalchemy catboost pydantic psycopg2 uvicorn

Quality Model Assessment:
In train model various metrics and their comparisons are presented.
The best model based on the metric HitRate@5 (the metric takes the value = 1 if the user liked 1 or more posts out of 5 posts, 0 if none of the 5 were liked) -- On test data, the catboost model showed HitRate@5 = 0.866
Start service
At the moment, the project is not invested in Docker (close to implementation), so you can start the service as follows:

1. We clone to ourselves locally:
  <git clone git@github.com:Sultan477/Recommendation-system-social-network.git>

2. create a virtual environment:
  python -m venv Recommendation-system-social-network

3. Go to the folder, the virtual environment starts, install the libraries:
  - cd Recommendation-system-social-network
  - .\Scripts\activate
  - pip install -r requirements.txt
  - request the .env file - where the key to the PostgreSQL service will be specified!

4. start service
  - cd .\FastAPI
  - uvicorn app:app

You can make the request in the browser or in Postman:
localhost:8000/post/recommendations/?id=200&time=2023-11-12 22:57:45
In this request template you can change the ID and time. Range of possible identifiers: 199 < id < 163206
