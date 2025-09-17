---
layout: post
title: How I Counted Digimon
subtitle: And Created a Good 3 Digimon Team
gh-repo: Alban-Maurel-HM/AlbanJekyll
gh-badge: [star, fork, follow]
tags: [test]
comments: true
mathjax: true
author: Alban Maurel
---

What is the average speed of all digimon? How many digimon have a certain attribute? What is a possible team I can use? I was tasked with answering these questions as! Here are my answers: 


![Crepe](startCode){: .mx-auto.d-block :}

First, I used this code to find both the average speed and the amount of digimons with a certain attribute.

```python
import csv
def count_digimon(column, specific): 
    with open("digimon.csv", "r") as f:
        reader = csv.DictReader(f) 
        speed = [] #list that I can later take average of
        count = 0 #amount with a "specific" attribute
        for row in reader:
            row["SP"] = int(row["SP"]) 
            speed.append(row["SP"]) 
            if row[column] == specific:
              count += 1
        speed_avg = sum(speed)/len(speed)      
        print("The amount of digimon with", specific, "is", count) #nice formatting
        print("Avg speed is:", speed_avg)
count_digimon("Type", "Vaccine") #example given
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.

## Local URLs in project sites {#local-urls}

When hosting a *project site* on GitHub Pages (for example, `https://USERNAME.github.io/MyProject`), URLs that begin with `/` and refer to local files may not work correctly due to how the root URL (`/`) is interpreted by GitHub Pages. You can read more about it [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). To demonstrate the issue, the following local image will be broken **if your site is a project site:**

![Crepe](/assets/img/crepe.jpg)

If the above image is broken, then you'll need to follow the instructions [in the FAQ](https://beautifuljekyll.com/faq/#links-in-project-page). Here is proof that it can be fixed:

![Crepe]({{ '/assets/img/crepe.jpg' | relative_url }})

<details markdown="1">
<summary>Click here!</summary>
Here you can see an **expandable** section
</details>
