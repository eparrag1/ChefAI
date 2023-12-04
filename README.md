# ChefAI

(Repository in development) <br>

The aim of ChefAI is to be a cooking aid for those trying home cooking and either using recipes they would like to add to, or making their own. ChefAI will suggest additional ingredients which could improve their dish, and may be ingredients they have not thought of. It will also give reminders of basic addins they may have forgotten. <br>

The current iteration of ChefAI uses a RNN with a Word2Vec embedding for next word prediction, where a list of ingredients is given as input, and ChefAI will predict more.


## Webscraping

This code uses two datasets: <br>
* 1M Recipes dataset (tracked down on a kaggle notebook, this was a bit tricky to find, but see e.g. https://luisdrita.com/recipe1m-dataset-2ecb62a43804) <br>
* BBC foods recipes (from webscraping https://www.bbc.co.uk/food)

The 1M recipes dataset is preprocessed in Recipe1M_Preprocessing.ipynb <br>
The webscraping is done in two parts, the first bbc_recipes.ipynb scrapes the recipes and bbc_ingredients.ipynb extracts the ingredients from these recipe links.

CHEF_AI.ipynb performs some preliminary analysis with this scraped BBC food data, where it simply looks at which ingredients appear frequently together.

## Next word prediction

BBC_Word2Vec.ipynb prepares the Word2Vec model to use as the embedding. The model will be trained with the ingredients lists for each of the recipes in the BBC food dataset, and the ingredients are already easily extracted. The 1M Recipes will use used to train the Word2Vec as these ingredients are used in context in the recipes themselves. The Word2Vec model also looks at bigrams (words which frequently appear together) as some ingredients are multiple words (e.g. olive oil, black pepper). <br>

ChefAI-RNN-with_embedding.ipynb then trains the model and shows the initial predictions. With the nature of the training the order of the ingredients given as input can have an effect on the next ingredients suggested, in a difficult to explain way. However, reshuffling of the input can be used to give more sets of suggested ingredients, and this will be looked at in the future. <br>

