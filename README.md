# Creation of an WKS Machine Learning Annotator & Deployment to NLU

## Learning Objectives

The objective of this tutorial is to train an ML annotator model using domain adaptation via a domain-specific training corpus, deploy the model to NLU to extract patterns, keywords from unstructured text. This use case is specific for the automotive industry but can be used for other domains as well. WKS can be used when base set of entity types from NLU are not sufficient.


## Prerequisites

- IBM Cloud account: If you do not have an IBM Cloud account, you can create an account [here](https://cloud.ibm.com/)
- Provision a Watson Knowledge Studio [instance](https://cloud.ibm.com/catalog/services/knowledge-studio?hideTours=true&?cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_Discovery-_-Watson_Developer_Website) within IBM Cloud & creation of a workspace.
- Basic knowledge of Watson Knowledge Studio process workflow & creation of roles by viewing [docs](https://cloud.ibm.com/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tokenizer).

## Estimated Time

It is recommended to annotate a variety of a large set of documents for greater accuracy however, estimated times are as follows:20 docs = 2 hours , 10 docs = 1 hour, 5 docs = 30 min and a small sample size will be used for this exercise.

## Challenge

Customers may have a build a domain specific machine learning model for their industry.

## Create Workspace

The default tokenizer is more advanced than the dictionary-based tokenizer; it uses machine learning to identify the tokens in the source documents based on the statistical learning it has done in the language of the source documents. It identifies tokens with more precision because it understands the more natural and nuanced patterns of language. The dictionary-based tokenizer identifies tokens based on language rules

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/1.png)

## Creation of a Type System for Domain Adaptation (Entity Types & Relation Types)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/4.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/1_beforeentityresized.png)

## Creation of a Dictionary for Domain Adaptation (specific entity type or rule class)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/7_dictionarysizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/8_dictionarysizing.png)

## Creation of Representative Document Sets for Building a Training Corpus

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/10_documentsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/11_addadocumentsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/12_documentsetsfilledinresized.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/14_createannotationsetssizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/15_annotationsetsizing.png)


## Perform Pre-annotation for bootstrapping Human Annotation

Rule Based Model(Run independently or train against ML model):
- Rule Editor: dictionary associated with rule class & regex for pattern matching
- Map entity types from type system to one or more rule classes(Versions)
- Rules based annotator creation & save for [deployment to WDS or NLU](https://cloud.ibm.com/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish#wks_rule_publish)

Rule-based model: Uses a declarative approach to finding entities in documents. This type of model is more predictable, and is easier to comprehend and maintain. However, it does not learn from new data. It can only find patterns it has been taught to look for.

Machine learning model: Uses statistical approach to finding entities and relationships in documents. This type of model can adapt as the amount of data grows.

Machine Learning Model:
- NLU API for annotation with predefined set of entity types
- Dictionary annotator(associate a dictionary with an entity type from the type system, creates an annotation for each mention in the text that matches a dictionary term)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/22_ruleeditorsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/23_dictionarysizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/dictionaryannotator.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/dictionaryannotatorconfirmation.png)

## Perform Human Annotation 

Human annotators submit annotated documents for review
- A mention is a span of text that is relevant in your collection data. For example, in a collection that contains documents about automobiles, terms like airbag, Ford Explorer, and child restraint system might be labeled by a machine learning annotator as relevant mentions
- Coreferences are mentions that mean the same thing, thus helping to ensure consistency when words are not identical. Examples of coreferenced mentions include the name of a U.S. state and its abbreviation, the name of a company and its acronym, or a person's name and a pronoun that refers back to that person
- Relations: A relation identifies a binary, ordered relationship between two entities. For example, in documents about automobiles, the machine learning annotator might use the relation “occupantOf” to identify people who are occupants of a vehicle. For another example, the relation “employedBy” might identify people and the company they work for.

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/17_annotationtaskresized.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/18_annotationtaskcreationsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/20_addannotationsettotaskresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/28_humanannotationinprogressresizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/29_fiatannotationresizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/30_inprogresssizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/31_completeannotationtaskresisze.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/32_completedannotationtasksresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/33_acceptannotationsetsresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/34_completedannotationtaskresize.png)

## Create Ground Truth

- For the purpose of this tutorial we will assume annotation quality control has been performed

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/40_inconflictresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/38_conflictcheckingresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/39_accepthumanannotatorsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/37_acceptannotationsetmsgresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/41_completedsetsresize.png)

## Train & Evaluate

- Training set: A set of documents that have been annotated through pre-annotation or by human annotators that is used to train the model. The goal of the training set is to teach the machine learning model about correct annotations, which includes teaching the model through text that was not annotated.
- Test set: A set of annotated documents that is used to test the trained model. After you run a test on the test set, perform a detailed diagnostic-purposed error analysis of the results. Close analysis helps you find weaknesses in the current model that can be addressed.
- Blind set: A set of annotated documents that is set aside and used to test the system periodically after several iterations of testing and improvement have occurred. To prevent accuracy from being tainted (for example, by making changes based only on annotations in known documents), blind data should be data that has not previously been viewed by users involved with creating the model.

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/42__trainingtestblindtophalfresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/44_trainingtestblindbottomhalfresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/46_MLmodelevaluationcomplete.png)

## Snapshot for Production Deployment & Continuous Improvement

- If there is only one working version of the model, create a snapshot of the current model. This versions the model, which enables you to deploy one version, while you continue to improve the current version. The option to deploy does not appear until you create at least one version.

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/48_deployversionsresize.png)

## Deploy to NLU after provisioning of NLU instance

- Identify & analyze semantic features of text input, including custom entities and relations unique to your domain
- [Working with deployed models](https://cloud.ibm.com/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing#customizing) 

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/50_nluprovisionresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/40b_deploymodelnluresizebox.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/41_deploymodelresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/49_deploymsgresize.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/45_finalshotdeployedresize.png)

Summary
In this tutorial guide, we:
- Defined a problem statement.
- Imported a document set and created a type Systems in WKS.
- Annotated the document set.
- Created, trained, and evaluated custom machine learning model.
- Took Snapshot of annotation component artifacts
- Deployed the WKS model to NLU.

This concludes the tutorial guide. I hope you found it useful.


