# Human-in-the-loop data annotation
**Moderator:** Maciej Szpakowski from [Researchably](https://researchably.com/)  
**Blurb**: 
_Who should come?_ 
Anyone building machine learning algorithms in fields with small amounts of training data or interested in building production-ready AI systems with humans in the back-end. 
 _Why should you care?_ 
 We all know how hard it is to get training data for anything else than distinguishing dogs from cats. This is especially true for Deep Learning, with its data-hungry models being out of reach for young ML startups. Come if you want to learn or share experiences around how to bootstrap a ML project/company with no data!
**Reading**: ["Accelerating Human-in-the-loop Machine Learning: Challenges and Opportunities" (Xin et al. 2018)](https://arxiv.org/pdf/1804.05892.pdf)  
**Keywords**: datasets, labeling, tools  

---


## Labeling sources
How do you label your data?
* In-house consultants
  * More control/trustworthy
* 3rd party labelers (e.g. Mechanical turk)
  * Problems with incentives: taskers will go through as quickly as possible until they are rejected
  * Foreign taskers-- sometimes language barriers
  * Craigslist as a venue to source trusted, private worker pools
* Costs
  * Training annotators-- typically background knowledge of task is necessary
* Tips
  * Cos might give free data for evaluation for their existing systems

## Data quality
How do you QA your datasets?
 * Set aside subsets of data to manually 
 * Build a culture of "data quality" among engineers, subject matter experts, etc. 
  * Build an internal leaderboard to track labeling events, corrections, etc.
* [TensorFlow Data Validation](https://www.tensorflow.org/tfx/data_validation/get_started)

## Labeling interfaces
* Might corrupt/bias labelers by including "hints" (e.g. AI-assisted labeling interfaces)
  * [REQUEST] for HCI related research about interface design here?
* Choice of language important to prevent _data feedback loops_
  * "How likely is this to be bought?" is highly correlated with "How many people have we shown this product to?"
*  High integration costs in third party tools (that often have incomplete feature sets)

## Beyond traditional supervised learning
* Transfer learning: pretrain on larger datasets
  * Can bootstrap on smaller vocabularies
* [Data programming](https://arxiv.org/abs/1605.07723)/[Snorkel](snorkel.stanford.edu) to create training sets with labeling functions via "weak supervision"


## Deploying domain experts
* For QA: "what would a concerning output of the model look like?"
  * Develop rules/automated warnings for red flags in labels/model outputs
* Generally better to start with more expensive + higher quality labels and optimize for cost later. Garbage in = garbage out.
* Careful using domain experts/clients are "benchmarks". People are sensitive to measuring their own accuracy!
* Some pilot customers/clients are often very willing to be domain experts!

