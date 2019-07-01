


> Written with [StackEdit](https://stackedit.io/).

After deploying the model there are two important topics:

- Maintaining 
- Monitoring 

### Why Model Monitoring and Maintenance?

We spend a lot of time and effort building a great model, it work great offline, so should expect it should work online to, right? Well, not quite. Let's look some real world cases that show us the dangers of not monitoring your models. 

So, here it is Tay. Tay was a chatbot released by Microsoft in march last year. It would suppose to be a millenial chatbot. What that means is Tay interact with users with ages ranges between 18 to 24, have conversations and then learn from those conversations. And an interesting thing happened when Microsoft released Tay. When Tay was released it said thinks such as "Hello Word!" or "Humans are super cool" but within 24 hours, Tay learned to tweet about really offensive thinks just interacting with the users on Twitter. So, what happened? 

Tay was trained in a great corpus of data, Microsoft has also released also chabots in China and Japan. But what happened here is that once the chatbot was released into the wild the training that was used to update the models changed a lot and therefore Tay ended up producing thinks that were clearly not the scientist intended for to do. 

Let's look another use case, which is facial recognition. We know about facial recognition about Facebook and  Google, these are 

## Principles and Causes of Model Decay

In the previous segment we talked about why is it important monitor and maintain models. In this segment we will talk about why model performance decay over time. 

So, to get some intuition about the problem, let's take a ten thousand feet view about what a model is and how it is generated. So, here on the screen we have a very pictorial depiction about what a model is:

[ picture ]

We take some input data { xi, yi}, we have some training algorithm, which is specific to the kind of model you are training 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzMDk4MTAwMV19
-->