# ML_CyberSec_Lab2

# Structure of Directories:

       |____model
            |____bd_net.h5
            |____bd_weights.h5

        |____data

            |____bd
                |____bd_valid.h5
                |____bd_test.h5

            |____cl
                |____valid.h5
                |____test.h5

        |____repaired_models
            |____B_prime_4.h5
            |____B_prime_4_weights.h5
            |____B_prime_2_weights.h5
            |____B_prime_10.h5
            |____B_prime_2.h5
            |____B_prime_10_weights.h5

        |____Lab2.ipynb

        |____Lab2.pdf

        |____Lab2_report.md


# Process to execute my Code

Please place the data and models in appropriate folders and create an empty repaired_models folder which can save the repaired models.
Link to the data is [here](https://github.com/csaw-hackml/CSAW-HackML-2020/tree/master/lab3).

# Conclusion

Our goal for this Lab was to  design a backdoor detector for
BadNets trained on the YouTube Face dataset using the pruning defense which was discussed in
class. My detector took as input:
1. B, a backdoored neural network classifier with N classes.
2. Dvalid, a validation dataset of clean, labelled images.

And the output G is a "repaired" BadNet. G has N + 1 classes, and given unseen test input, it must output the correct class if the test input is clean (the correct class will be in[1, N]) and class N + 1 if the input is backdoored.

My model's performance results are given in the Lab2_report file.

There are three main takeaways that I gathered from this project:

1. The attack success rate for the original B model is greater that its clean classification accuracy which shows that BadNet model has good efficiency in attacking.

2. There is a possibility for **Pruning Aware Attack** which is "the evasion of the pruning defense by concentrating the clean and backdoor behaviour onto the same set of neurons" as stated in [this paper](https://moyix.net/finepruning.pdf) which leads to a quicker drop in clean classification accuracy than attack success rate before the validation accuracy drops below the original accuracy by 4%. 

3. When the difference between validation and original accuracy drops below 10%, the attacks success rate is significantly lower than clean classification accuracy but consequently, the clean classification accuracy is also lower when compared to 2% and 4% accuracies which means **pruning-aware attck** is occuring which means the same neurons work for both clean data and posioned data. 

What we can infer from the results of this lab is that **pruning defense** is not very effective in detecting Backdoors for BadNets trained on the YouTube Face dataset. Further research points towards using "Fine pruning defense" which is described in the linked paper.

# References

[1] [Fine-Pruning: Defending Against Backdooring Attacks on Deep Neural Networks](https://moyix.net/finepruning.pdf)
