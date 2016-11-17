# Generate Unique Random Data in Apache JMeter

In this JMeter tutorial, you are going to learn my simple trick about how to create unique random data parameterization in JMeter. Data parameterization is must to have in the test plan to simulate real world scenario. It is a good practice to test the performance of the application by having more realistic sets of data in the script. There are lots of tutorials available in internet about data parameterization in JMeter, but this article explains a simple way to create unique random data parameterization in JMeter.


# Before you start

Before you start creating test plan, identify how many columns of data you have in your data sheet. More columns of data, more cumbersome it is. This is just a simple trick, and it will not suit if you have more number of columns. I suggest to have maximum of five to ten columns of data.


# Now Samplers part

We are going to leverage User Defined Variables sampler in order to generate unique random data parameterization. If you have two columns of data, you need to have 3 User Defined Variables in your test plan.

1 User Defined Variables will have the number of columns of test data with Random functions
‘N’ User Defined Variables will have the actual test data


# Now Design part

Assume that you need to generate unique random values for below test data.

ImageNumber - Total number of rows are 55
HashtagNumber - Total number of rows are 10
DataTimeNumber - Total number of rows are 55


First step is to add User Defined Variables (name it as Reference User Defined Variables) and add the test data columns and random functions as shown below.

Subsequent steps would be to add User Defined Variables for each column of data. 

Important Note is to have the serial number at the end of the variable name. E.g. datetime1,datetime2, and so on

# Now execution part

Next step is to send the randomly uniquely generated test data in your request. To do so, you need to add the below syntax in your test plan.

${__V(hashtag${MYHASHTAGNUMBER})}
${__V(datetime${MYDATETIMENUMBER})}

Above syntax will retrieve the randomly unique data from the User Defined Variables sampler and send it your requests.

# Limitations

Above trick will work only the random generated number are not repeating again. 
You can increase the randomness by having more number of test data. It is quite easy to generate the variable names using Excel spreadsheet program.
