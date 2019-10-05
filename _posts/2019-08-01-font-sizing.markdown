---
title: Automatic Font Size Fitting
layout: post
date: '2019-08-01 11:17:20 -0700'
tags:
- UI
- Design
thumbnail: cover_font_fitting.svg
---

If you are like me, a developer of UI/UX of apps, you have probably faced difficulties with finding the right font size for a dynamic textual content. For those who never have encountered this problem, I will present my case.

I was creating a quiz app that retrieves questions from a web server. It displays the question in a particular part of the screen with fixed dimensions, as shown here :
![](/assets/article_pic/screen_app_font_1.png)

Some questions can be really long and some can be really short while the space allocated to display the question is limited. An automatic fitting system would solve that problem by changing the font size when the question changes. Here are screenshots of the app before and after the use of the automatic fitting system.
![](/assets/article_pic/screen_app_font_2.png)

Some Math
Who said you don’t need math to create UIs ?

This part explains the different constraints and how we can deduce the font size from the given data. We want to adjust the font size automatically for a given question and given dimensions of a container.

* **width** : the fixed width of the container of the question
* **height** : the fixed height of the container of the question
* **number** of **letters**  : the length of the question


These two equations sum up the idea of the automatic fitting system.
![](/assets/article_pic/font-sizing/formula1.png)

The objective is to explain these variables a bit more to be able to isolate the font size.

The first one is the line height. The ratio between the line height and the font size depends on the selected font, but a good approximation is to take 1.5 :
![](/assets/article_pic/font-sizing/formula2.png)

From the number of letters of the question, a variable we have access to, we can write :
![](/assets/article_pic/font-sizing/formula3.png)

Putting it all together :
![](/assets/article_pic/font-sizing/formula4.png)

We can work out (2) to get the expression of the number of lines :
![](/assets/article_pic/font-sizing/formula5.png)

By injecting the last result in (1), we obtain :
![](/assets/article_pic/font-sizing/formula6.png)

We now can express the font size depending only on our given variables :
![](/assets/article_pic/font-sizing/formula7.png)

Implementation
The implementation is pretty straight forward since the equation is really simple. It only requires setting the font size in Javascript, since the font size is supposed to change without a reloading of the page.

For my app, I also decided to set a maximum size to the font, in order to avoid a font size too big when the question does not contain many letters. Make sure to not forget using a round function to generate an integer.

Here is the code I used in React Native :

```jsx
{% raw %}
<Text style={{
  fontSize: Math.min(Math.round(
      Math.sqrt((config_dimensions_blocs.dimensions_question_text.width *
          config_dimensions_blocs.dimensions_question_text.height) /
          (this.props.question.length * 1.5)
      )
    ),
    25
  )
}}>
{this.props.question}
</Text>{% endraw %}
```

I might try to make a module out of this system since it is really useful, especially when it comes to building responsive and dynamic UIs.

Don’t hesitate to comment if you have any questions about implementing it.