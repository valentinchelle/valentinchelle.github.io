---
title: Using AI to counter depression
layout: post
date: "2019-09-29 11:17:20 -0700"
tags:
  - Deep Learning
thumbnail: feeling_down_cover.svg
extract: A method to counter depression with deep learning models.
time_to_read: 10 min
---

> I have worked the past few months on analysing emotions with deep learning models in order to detect depression. I also elaborated some ways to counter depression on social networks when it is detected. This article aims to establish some methods that could be applied to detect and mitigate depression on social networks. I won't enter into details such as the coding because I want this article to be accessible for any type of background, since the importance here lies in people being aware of these techniques.

## The need to counter depression

Social networks are becoming a huge part of current human interactions. People publish publicly their thoughts, feelings and emotions. And they would interact more often with people feeling the same way as them. <b>Hence, depressed people might interact, follow and share content with other depressed people</b>. It creates some kind of vicious circle, where it becomes harder and harder to get out of the depressive period.

## They have the data and the resources, I have the methods

Social Networks, now at the center of our life, have the responsibility to take care of their users. These companies have enough data to recommend you the smartphone you would most likely buy and they can do enough efforts to make you think you actually need that new smartphone. That data, and those efforts, could be used to help the users with problems like depression, and I'm going to show you how it can be done. So now Facebook, Twitter & Cie, you have no more excuses ;)

## AI and Emotions

Here are the three problems that come up when we want to mix artificial intelligence and depression.

### 1. Emotion Classification

The emotion classification simply consists of attributing a class of emotion to a message. For example, “i love you” is supposed to be classified as a love message.
To give you an idea, here are the classes of emotion I considered in my study :

<table>
	<tr>
		<td>
			<b>Fun</b>
		</td>
		<td>
			Haha that afternoon was so great 
		</td>
	</tr>
	
	<tr>
		<td>
			<b>Happy</b>
		</td>
		<td>
			I'm so glad I received a new phone
		</td>
	</tr>
	
		<tr>
		<td>
			<b>Love</b>
		</td>
		<td>
			I miss you and I can't wait to see you !
		</td>
	</tr>
	
		
		<tr>
		<td>
			<b>Neutral</b>
		</td>
		<td>
			This is an interesting article.
		</td>
	</tr>
	
		
		<tr>
		<td>
			<b>Worry</b>
		</td>
		<td>
			I'm scared I won't have a good grade.
		</td>
	</tr>
	
		
		<tr>
		<td>
			<b>Sadness</b>
		</td>
		<td>
			I don't like when it rains, it makes me feel down.
		</td>
	</tr>
	</table>

### 2. Emotion Prediction

The emotion prediction tries to predict the emotion of the next message of a user by considering the emotions of the few past messages of this user. This is an indicator of the user's mood on the short term.

<table>
	<tr>
		<td>
			<b>Past Emotions</b>
			</td>
				
		<td>
			<b>Prediction</b>
			</td>
	</tr>
	<tr>
		<td>
			Sad > Neutral > Sad 
			</td>
		<td>
			Sad
			</td>
	</tr>
	<tr>
		<td>
			Neutral > Happy > Neutral
			</td>
		<td>
			Happy
			</td>
	</tr>
	
</table>
### 3. Depression Detection
The depression detector tries to detect whether or not a user is going through a depressive period by considering the whole history of their messages' emotions. This is a global indicator of the user's mood.

<table>
	<tr>
		<td>
			<b>Past Emotions</b>
			</td>
				
		<td>
			<b>Prediction</b>
			</td>
	</tr>
	<tr>
		<td>
			Sad > Neutral > Sad > Neutral > Worry > Worry
			</td>
		<td>
			Not Depressed
			</td>
	</tr>
	<tr>
		<td>
			Sad > Worry > Sad > Neutral > Sad > Sad
			</td>
		<td>
			Depressed
			</td>
	</tr>
</table>

## Building a Dataset of Emotions

> For those of you who are not familiar with AI, such models to predict or classify need to be trained. It means that we have to find the right parameters that will give the right prediction. To do that, we need some data on which we can first train the models and try to optimize their performances. For instance, to train the emotion classifier, we need a list of numerous tweets associated to a class of emotion. It means we need a list of happy tweets, a list of sad tweets, etc. All these lists are then gathered to form the training dataset. Once the model is trained, we can then apply it to classify tweets for which the emotion is not given.

The whole question is how to get a training dataset ? Do we have to pay people to classify by hand the emotions of thousands of messages one by one ?

To answer this question, I chose to work on Twitter. Something really great about Twitter <strike>is being able to follow the tolerant tweets of an orange man with a blond hairpiece</strike> is its system of hashtags such as <i>#covfefe</i> and emoticons.

<b>Instead of paying someone to label one by one the messages, I just "guess" the emotion of a tweet by looking at the hashtags and the emoticons in it</b>. I make a list beforehand of hashtags and emoticons associated to a particular emotion and I retrieve the tweets containing only those.

<table>
 <tr>
	 <td>
		 #enjoy, #enjoylife, #relax, #laugh, #lovelife, #sohappy, #excited,#feelgood,#happier,#goodmood, #joy, 🙂, 😀, 😛, 😉
	</td>
	 <td>
		 Happy
	 </td>
	</tr>
	<tr>
	 <td>
		 #sadness,#sad,#depressed,#alone,#lonely,#sadquotes, #depression,#anxiety,#crying,#upset,#lifesucks,  😞, 😕, 😢, 😞
	</td>
	 <td>
		 Sad
	 </td>
	</tr>
</table>

## Counter the Depression

![](/assets/feelingofjoy.svg)
If social networks could set a depression detection as presented above, that would already be great. It would then be very simple to at least recommend helpful resources to depressive users.

Not only can my work be used to detect depression, but it can additionally be applied with ease to actively mitigate the spread of depression. Here are some methods I thought about, without having to do much more effort.

### 1. Limiting interaction with depressive content

The first way would be to offer to the users, with their consent, a way to limit their exposure to sad content if they are classified as a depressed user. This would limit the vicious circle effect. This would require to be able to classify the content as as sad or happy, but this is something that has been done many times in the past years, so this is easily doable.

### 2. Increase exposure to happy content

A complementary way would be to recommend to the depressed user more happy news and content more generally.

### 3. Predicting Depression

The work I did in terms of prediction was not very consistent : I had almost no resources, and I did not have access to much data.
But I am pretty sure that some teams could manage to accurately predict more than just the next emotion. This prediction, of the next messages, could then be fed in a similar depression classifier to be able to identify depression before it actually occurs. The efficiency of the methods mentionned above to mitigate the effects of the depression would sensibly increase.

### 4. Other ways to help

I am an engineer, and I know almost nothing about depression. I tried to think about methods to counter depression from an engineering point of view, but they are not perfect, especially considering that <b>people might not want the social networks to control their feelings</b>. However, there are many specialists in the world that probably have better ideas on how to help depressed people online. They could probably come up with smarter ways to more directly help people suffering from depression.

## Conclusion

I hope this article presents depression detection as easy, because it is actually very easy to create models that detect depression. The trickiest part, as an engineer, is to find the right thing to do in order to counter depression. And it is probably that point that would require the help of some specialists. But the technical part, at least, is easy to implement.

For those of you who want more details, here is my master thesis : <a href="/assets/Project_MSC_Valentin_Chelle.pdf">Deep Learning For Emotion Analysis</a>.
