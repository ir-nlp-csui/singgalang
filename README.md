# singgalang
An auto generated NER dataset of 48K sentences

The datasets conforms with the dataset format of Stanford-NER.

Four named entity classes are used:

    "Person" for person names
    "Place" for place names
    "Organisation" for organization names
    "O" for others
    
## References

The dataset may be used for free, but if you want to publish paper/publication using the dataset, please cite these publications: 

* Ika Alfina, Septiviana Savitri, and Mohamad Ivan Fanany, ["Modified DBpedia Entities Expansion for Tagging Automatically NER Dataset"](https://ieeexplore.ieee.org/document/8355036), in Proceeding of 9th International Conference on Advanced Computer Science and Information Systems 2017 (ICACSIS 2017).

* Ika Alfina, Ruli Manurung, and Mohamad Ivan Fanany, ["DBpedia Entities Expansion in Automatically Building Dataset for Indonesian NER"](https://ieeexplore.ieee.org/document/7872784), in Proceeding of 8th International Conference on Advanced Computer Science and Information Systems 2016 (ICACSIS 2016).


## How to create NER model using this dataset?

We suggest you to use the Stanford NER library.<br>
The steps to create NER model using Stanford NER library are as follows:
1. Download [Stanford-NER](https://nlp.stanford.edu/software/CRF-NER.shtml).
2. Download the dataset and its properties file (file with .prop extension)
3. Use Stanford NER classifier to create the model. <br>
   For example: <br>
      java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop singgalang.prop <br>
      
      I recommend to increase the heap size so you can train the dataset on computer with limited RAM. Add option like "-Xmx1024m" on the command, for example:<br>
      
      java -Xmx1024m -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -prop singgalang.prop <br>
      
      if this still doesn't work, increase the number. For example: "-Xmx8000m". This works for me :)

   Let say this step will create a NER model file named "idner-model-singgalang.ser.gz"
 
4. Create or use a testing dataset. Lets say the file name is "testing.txt"
5. Evaluate the NER model using Stanford NER library <br>
   For example:<br>
        java -cp stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -loadClassifier idner-model-20k-mdee.ser.gz -testFile testing.txt 
   

## Contact
ika.alfina [at] cs.ui.ac.id
