# Spark API:
* Distributed DataFrames
* Dataframe / SQL
* Dataset
* Old RDD (for broadcasting)

# Exercise:
Implement `deleteIfExists` method which deletes parquet files both locally and on the cluster (*i.e.* hdfs)

# Collaborative Filtering:
Can one easily predict new User-Feature vectors without redo-ing ALS on the entire dataset?

# Saturday March 24:
## Anna - Google


## Charles Parker - BigML - AutoML
Interesting philosophical points on ML:
- ML is just an abstraction on top of data, the same way a steering wheel is an abstraction on top of a steering system.
- However, half the battle is to also be able to interact beneath the abstraction to ask the model why it is doing what it's doing
- Meta ML is an interesting idea, the idea of matching meta characteristics of a dataset to predict which types of models will work the best --> though he doesn't have the gut feeling it will generalize well

## Ebay- boring
Too high level

## Online Recommendations - Adobe Research
~ half team working on computer vision
~ half

Q. Why is Adobe interested in research?
<br>A. Collect tons of click data

###  What is a Rec. System?
* training data is past interactions
* rec system tries to exploit --> best recommendation for User
* problem, if deploy online, postive feedback loop --> not learning anything about the user
* Therefore, need some explorative recommendations in addition to exploitative recommendations!
* EXploration by modelling uncertainty about the user
<br>.............<--[doughnut]-->
<br>......<-----[pizza]-------------->
* Recommendation based on upper confidence bound (UCB)
* In the above, recommend the pizza instead of the doughnut because it might be more valuable

### Stochastic Multi-Armed Bandits:
* 2002 Auer et al, greedily play machines based on UCBs

#### Example (Online Learning):
* Buying 4 of K possible lottery tickets per day
* K!/(K-4)! possible selctions
  * Takes ~5 yeasrs to explore combinations of lottery tickets in his story with k=8, one combo per day...
* CombUCB1 -> faster model
  * Compute UCB on the expected rewards of all tickets
  * choose the omst rewarding Dataset
  * observe noisy reward of all chosen tickets
  * update statistics associated with each ticket
* This is a near optimal algorithm for any combinatory set
* [Tight Regrest Bounds for Stochastic Comb...](http://proceedings.mlr.press/v38/kveton15.pdf)
* Algorithm fails because of positive feedback loop?

Fix = Cascade Model
* [combinatorial cascading bandits](http://proceedings.mlr.press/v48/lif16.pdf)

* Lower ranked items not very good, user never gets to them... ;-(
* See "regret" vs step T plots

* What about external aspects that affect recommendations (*e.g.* outside weather, time of day, *etc.*)


## Dimensionality Reduction for Guaranteed Display Advertising - Antonín Hosk...

### Guaranteed Display Advertising:
(customer)
> I would like 100000 males between the age 25-30 who are interested in clothing to see my ad in April

(sales agent)
> Let me check...
I can sell that to you for price €x

(should take on the order of seconds)

In total: 312521952198519251258129138928323 possible choices

* Going through one month of impression logs takes 10s of minutes on a cluster

PCA to come up with user groups - looking for solution that:
* looks at history of impressions
*

Sex=male | Sex=female | OS=android | Interest=clothing | ...
----|----|-----|-----|----
x | | | x |
 | x | x | |

 * Aggregate to form vectors over particular time period... the do PCA to compress...

 * Now one can add up the impressinos for each PCA vector over time, and reduce the computation time to find out the impression rate for each segment!


## Sepp Hochreiter - Deeep learning!!!
* One of the developers of LSTMs
* AI > ML > DL

> If AIs have access to text, they have access to the knowledge of humanity.

* [Self normalization networks](https://arxiv.org/abs/1706.02515) allows for deeper feed forward networks that perform better (deep conventional FNNs not that successful)
* SeLu (Scaled Exponential Linear Units)

$f(x) = \lambda \left \{x, if x>=0$
...

* SeLu is the activation function of a self normalizing network
* Coulomb GANs

RL:
* MC tree search if env. deterministic
* Otherwise, SARSA / Q-learning, too many problems...
* Forget about the above --> use .... Rainbow, and a bunch of deep mind hacks +

> Policy Gradient is an evolutionary algorithm that doesn't work well

## The Alexa Prize -


## Prospects in Quantum Enhanced Machine Learning:
- Javob Bianotte, Deep Quantum

* when should we act, how
* what is the future, how far away is it?

* Advanced model - disipative annealer (~45 spins)

Why Quantum Software?
* None of the algorithms work yet (i.e. Shorr's algorithm)

* Discovered a new condensate --> Quantum MAchine Learning (lol)- --> all the rage
> Many academics are just lying to everybody.

* IBM - 50 qubits... (kinda works)
> the most impressive

* D-Wave (2000 spin annealer)
> Have sort of been saying what they'll do for too long

* Google (75 qubits)... (doesn't think it works)

> I'm very sure Q-computing will change things... replacing a computer algorithm with a physical process

> Physical processes naturally minimize free energy

(Think Gibb's Sampling) --> Training deep NN by Gibbs sampling on a Quantum chip --> a very real early application

Check out the twitter image, "classes of quantum enhanced devices" - programmability vs. difficulty

NP-hard vs QMA-hard

### Computational Phase Transition:
Is the problem satisfiable or not. (wiki Satasfiability)

> Most Quantum hardware startups not going to touch Q-stacks.
> We're giving away ours for free, "Qrystal."

When do you think the quantum computers will be good enough to break RSA?
> Bullshit! Classical algorithms can also break RSA.... cryptography will adapt, no big deal... there are decades before a change needs to occur.

What's there in Skolkovo, regarding quantum computing hardware?
> The wonderful thing about being a theoratician ....

What will be the first global “killer app” for QC?
> Optimizers

> From Walla Walla Washington

Do you think Quantum Computers will be common and affordable in the near future?
> No way... Google is lighting money on fire and will want some ROI... this stuff will change ML with Gibbs sampling but Google is not going to let their findings go (they're completely going for it).

Some peopple say consciousness is a quantum state, what do you say about it?
> I say they're lunatics.

Why do you say DWave has spin annealers and not quibits?
> They are making a system which anneals to its ground state.  Once they have some time dependent control, I'll update them to qubit status.

How can you talk so easily about quantum computation if the problem of error detection is still not solved? Parity bit is not an option in quantum computers...
> Well, not proven that we will need it... but everything we do relies on this so... that's why there are only pictures of these chips.

## Putting Research into Practice - Radim Rehurek - rare-technologies

* Focuses on the intersection between engineering and research
  * Amazon.com
  * Hearst
  * Autodesk
  * Signal Maritime
    * maritime logisitcs
      * semi structured emails, need to extract meta data about vessels
      * deep NN on character level

> Uncanny valley of freelancing:

* profil and productivity **drops** after adding people

> With love, you let it go and if it's good it comes back... that's my take on research, if it's good it'll come back to me so I don't follow everything.

> For businesses it's all about repeatability.

> ScaleText: Gensim on Steroids

> Cannot build software to replace data scientists... because every important client has their own data science team.

### GDPR:
PII tools, finds where the sensitive data is and optionally masks it.

### The Bridge of Respect:
* Pointy haired managers
* ivory tower researchers
* annoying marketers
* tunnel vision engineers
* sleezeball salesmen
* crooked lawyers

> Everybody is running as hard as they can so show a little respect.

## GDPR & ePrivacy rule as an EU gift to non-EU technological competitors
(Gauss Algorithmic)
*

## ML for Social Good -

### Gauna Mine identification:
* Transfer learning to learn: mine, not mine, cloud (from satalite images)

* Transfer learning as a service: https://customvision.ai/
* Deployed on Kubernetes cluster in Azure
  * Azure file share
  * Kubernetes
  * Queues in Redis
  * MySQL

### Red Cross Refugee Locator:
* Tried face rec API in Azure, didn't work because only a limited number of faces were supported
* No permission for online solution
* Facenet on premise was too heavy
* Face_recognition package (python package) was the best

### Kitty Wig bird counting:
* Nest of cliffs and in bulk

2015 - Faster R-CNN good for object segmentation
Better - SSD single-shot detector

Tensorflow has a great object detection API

### Final Thoughts:
* Let the  
* Know your problems
* Users often don't need the best answer
* Buy and build (but for free)


## Gotchyas:
* [Data Version Control](https://dataversioncontrol.com/) - like persistable
* Annotating dataset
  * `Data Programming` - haizy research @ Stanford Univ.
  * A paradigm for getting labels
  * [snorkel](https://github.com/HazyResearch/snorkel)
  * Generate labels for your supervised learning algos
* Sensei
  * dockerizes data science projects --> makes them reproducible and able to deploy quickly --> output to cloud storage
  * Active Learning
  * This is something that CEAi is kind of building
