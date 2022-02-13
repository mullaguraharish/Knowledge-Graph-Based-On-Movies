# Knowledge Graph Based on Movies
## An Information-Retrieval Project
 
## Problem Statement :
- Information Extraction is a process of extracting information in a more structured way i.e., the information which is machine-understandable. 
- It consists of sub-fields that cannot be easily solved. Therefore, an approach to store data in a structured manner is required for easier access.

## Problem Solution:
* Knowledge Graph is a structured way in which a set of three-item sets called Triple is used. 
Here, the set combines a subject, a predicate, and an object. 

* We will build a knowledge graph using Python and Spacy. Knowledge graphs put data in context via linking and semantic metadata and this way provide a framework for data integration, unification, analytics, and sharing.

## Project Description:

- The knowledge graph represents a collection of interlinked descriptions of entities – objects, events, or concepts. 
- The edges are the connections interfacing these elements to each other. 
- We will extricate these components in an unaided way, i.e., we will utilize the punctuation of the sentences.
- The primary thought is to experience a sentence and concentrate on the subject and the item as and when they are experienced. 
- First, we need to pass the text to the function. The text will be broken down and placed in each token or word in a category. 
- After that, we have arrived at the finish of a sentence, we clear up the whitespaces which may have remained, and afterward, we’re all set, we have gotten a triple. 
- For example, the statement “IIIT Sri City is categorized as a Tier-1 college” will give a triple focus on the main subject(IIIT Sri City, categorized, Tier-1 college). 
- The knowledge graphs gives information about singers, writers and movies released. 
- There is a movie recommendation system which will give most recommended movies similar to the given movie.

## How to run the code : 

- The dataset is obtained from https://drive.google.com/drive/folders/1IpCO8C6V2puZLx5CTgy3HAV7Zps6nF6F 

1) Hit the URL: https://colab.research.google.com/drive/1MVY538WLcRjCzgGO_mpvwcpYhwngwy2s?usp=sharing

2) After opening the code, In the left menu bar select files and upload the dataset.

3) Either leave the default path that works or copy the path of dataset in the candidate_sentences = pd.read_csv("/content/wiki_sentences_v2.csv")

4) Once the data is loaded the code gives the knowledge graphs of movies like singers, writers and movies released. 

5) It also gives the movie recommendation by preprocessing by replacing Nan values with 0 and then taking user vote ratings and 
number of users voted. After that we use knn for nearest neighbors and by creating a function fet_movie_recommendation we get 
the movie recommendation similar to the given movie.

**For more details about the project please refer to [**"Project Description.pdf"**][1]**

[1]: https://github.com/mullaguraharish/Knowledge-Graph-Based-On-Movies/blob/main/Project%20Description.pdf "Title"


## Functionalities and Components of the project:

<pre>
1) Import Libraries :
Import re, pd, bs4, requests, spacy.

2) Read Data :
Read the CSV file containing the Wikipedia sentences

3) Entity Pairs Extraction :
To build a knowledge graph, the most important things are the nodes and the edges between them.
These nodes are going to be the entities that are present in the Wikipedia sentences. 
Edges are the relationships connecting these entities to one another. We will extract these elements 
in an unsupervised manner, i.e., we will use the grammar of the sentences.

4) Relation / Predicate Extraction :
For example, in the sentence – “Sixty Hollywood musicals were released in 1929”, 
the verb is “released in” and this is what we are going to use as the predicate 
for the triple generated from this sentence.

5) Build a Knowledge Graph :
We will finally create a knowledge graph from the extracted entities (subject-object pairs) and 
the predicates (relation between entities).
kg_df = pd.DataFrame({'source':source, 'target':target, 'edge':relations})

   - Based on the data crawled and collected for Actors and Movies, I created a knowledge graph 
      to perform "Entity-Entity pair based on Relation" Query.
   - The sentences were tokenized and the Entity-Relation-Entity were identified 
      and put into the Knowledge Graph
   - The knowledge graph was visualized using Networkx

6) Removing Noise from the data :
We will reduce the noise by adding some filters for the final dataset.

   - To qualify a movie, a minimum of 10 users should have voted for a movie.
   - To qualify a user, a minimum of 50 movies should have been voted by the user.

7) Removing sparsity :
Applying the csr_matrix method to the dataset 
csr_data = csr_matrix(final_dataset.values)
final_dataset.reset_index(inplace=True)

8) Making the movie recommendation system model :
We will be using the KNN algorithm to compute similarity with cosine distance metric 
which is very fast and more preferable than pearson coefficient.
knn = NearestNeighbors(metric='cosine', algorithm='brute', n_neighbors=20, n_jobs=-1)
knn.fit(csr_data)

9) Making the recommendation function
get_movie_recommendation('Iron Man')
</pre>

## Conclusion:
We extracted information from a given text in the form of triples and build a knowledge graph from it. 
However, we restricted ourselves to using sentences with exactly 2 entities. Even then we were able to build quite informative knowledge graphs. 

We have described how KGs can help IR by discussing several entity-centric IR tasks and the role of KGs in each. 
Specifically, we discussed entity linking, document retrieval, entity retrieval, entity recommendation, and relationship explanation.
Thus, we were able to build a Knowledge graph for the movie's dataset.

## Group Members :

<pre>
Harish Mullagura - S20190010124 - harish.m19@iiits.in
Anirudh Jakhotia - S20190010007 - anirudh.j19@iiits.in
Neeraj Dusa - S20190010047 - neeraj.d19@iiits.in
V Venkata Kalyan - S20190010193 -venkatakalyan.v19@iiits.in
</pre>
