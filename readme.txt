Project 2 : Naive Bayes Classifier
by Cal Blanco for CSE 107

Files (important files):

    data : contains given training and testing files 

    naive_bayes.py : this was the main file I made changes to

    Project2_ProgramWriteup_CalBlanco.pdf : my program write up

    I removed the C++ and C code. I don't know if that is okay but 

    naive_bayes.py:
        important variables:
            num_train_hams:int  The number of ham emails
            num_train_spams:int  The number of spam emails 
            word_counts_spam:dict  A dictionary s.t word_count_spam[IN] = # of times IN appeared in spam emails
            word_counts_ham:dict  A dictionary s.t word_counts_ham[IN] = # of times IN appeared in ham emails 
            HAM_LABEL:str  A string that represents HAM, is returned when we predict an email to be ham
            SPAM_LABEL:str A string that represents SPAM, is returned when we predict an email to be spam 


    FUNCTIONS:

    fit( train_hams:list , train_spams:list)

        This function takes in our training input data to generate our probabilities for words in emails being spam or not


        @params:
            train_hams is a list of emails that are "ham" aka not spam 
            train_spams is a list of emails that are spam


        @nested functions
            
            get_counts(filenames:list)
                @param: filenames:list  A list of input files (used on train_hams and train_spams)

                Get the word set from each file in filenames and append to one large list W 

                Go through each word in W and and add it to a output dictionary out_count
                    if the word is present as a key in out_count increment its word count 
                        else add the word to the outcount and set its count to 1 

                @return out_count 
        

        get_counts is used on train_hams, and train_spams in order to populate the class variables
        word_count_spam, and word_counts_ham

    
    predict(filename:str)
        
        Take in a file as input. Using the word set from that file, determine if the file(email) is Ham or spam

        @param : filename:str  The input file (email)

        Generate the wordset from filename and placed into a list IW 

        The formula for Bayes Theorem is P(A | B) = P(B | A) * P(A) / P(B)

        in our case we want to determine the probability P(spam | IW) that the file is spam given the words in the file. We use bayes theorem because we have 
        a value for P(IW | spam) and P(IW | ham)

        np.log is used on the probability quantities to prevent underflow
        and laplace smoothing is used to prevent problems from unseen words

        if P(spam | IW) is greater than P(ham | IW) then the probability the email is spam was larger than the probability of ham
            @return SPAM_LABEL
        else:
            @return HAM_LABEL

        

    
         