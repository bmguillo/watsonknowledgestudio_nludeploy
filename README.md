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

Customers may have a need to modify the type system that they have created after they have deployed their model to NLU as a continuous training/testing practice for greater optimization and accuracy of the model.

## Create Workspace

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/1.png)

## Creation of a Type System for Domain Adaptation (Entity Types & Relation Types)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/4.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/2_entitytypes.png)

## Creation of a Dictionary for Domain Adaptation (specific entity type or rule class)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/7_dictionarysizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/8_dictionarysizing.png)

## Creation of Representative Document Sets for Building a Training Corpus

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/10_documentsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/11_addadocumentsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/12_documentsetsfilledinresized.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/14_createannotationsetsizing.png)
![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/15_annotationsetsizing.png)


## Perform Pre-annotation for bootstrapping Human Annotation

Rule Based Model(Run independently or train against ML model):
- Rule Editor: dictionary associated with rule class & regex for pattern matching
- Map entity types from type system to one or more rule classes(Versions)
- Rules based annotator creation & save for [deployment to WDS or NLU](https://cloud.ibm.com/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish#wks_rule_publish)

Machine Learning Model:
- NLU API for annotation with predefined set of entity types
- Dictionary annotator(associate a dictionary with an entity type from the type system, creates an annotation for each mention in the text that matches a dictionary term)

![test](https://github.com/bmguillo/watsonknowledgestudio_nludeploy/blob/master/img/10_documentsetsizing.png)


