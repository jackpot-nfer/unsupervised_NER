# Unsupervised NER (prototype)
Prototype unsupervised implementation NER using BERT's MLM and wrapper around [Dat Quoc Nguyen's POS tagger/Dependency parser](https://github.com/datquocnguyen/jPTDP)


[Medium post describing this method](https://towardsdatascience.com/unsupervised-ner-using-bert-2d7af5f90b8a)

![Image from Medium post on unsupervised NER ](./assets/NER.png)


# Installation 

**1) Install POS service using https://github.com/ajitrajasekharan/JPTDP_wrapper.git**

*Make sure to run **both** services in the install instructions*

Confirm installation works by 

    $ wget -O POS "http://127.0.0.1:8073/John flew from New York to Rio De Janiro"
    
   The output POS file should contain
  
  ![The output POS file should contain ](./assets/POS.png)
  
 
 **2) Install BERT descriptor service using https://github.com/ajitrajasekharan/bert_descriptors.git**
 
 Confirm installation works by 
 
   $ wget -O DES "http://127.0.0.1:8087/dummy/John flew from entity to Rio De Janiro"
   
   The output DES file should contain
   
 ![The output POS file should contain ](./assets/DES.png)
 
 


**3) Install BERT vector clustering service using https://github.com/ajitrajasekharan/bert_vector_clustering.git**
 
 Confirm installation works by 
 
  $ wget -O ENT "http://127.0.0.1:8043/Miami Chicago Florida Albuquerque Houston California London Boston Austin Mexico"
  
   The output ENT file should contain
   
   LOC LOC LOC LOC LOC LOC LOC LOC LOC LOC
  
 
 
 **Additional notes**
 
 - Step 1 above requires python 2.7 environment wheareas steps 2 and 3 requires python 3+. Step 2 requires pytorch environment. So it is best to run these services separately in different environenments (I used [screen](https://linuxize.com/post/how-to-use-linux-screen/)  to separate them). 
  
 
# Usage

The unsupervised NER tool  can be used in three ways. 

1) to tag canned sentences (option 1)
     - $ python3 main_ner.py 1 
2) To tag custom sentences present in a file (option 2)
    - $ python3 main_ner.py 2 sample_test.txt
3) To tag single entities in custom sentences present in a file (option 3) where the single entity is specified in a sentence in the format name:__entity__. Concrete example: Cats and Dogs:__entity__ are pets where Dogs is the term to be tagged.
    - $ python main_NER.py 3 single_entity_test.txt
    
    
    
 
  

# License

This repository is covered by MIT license. 

[The POS tagger/Dep parser that this service depends on is covered by a GPL license.](https://github.com/datquocnguyen/jPTDP/blob/master/License.txt)
