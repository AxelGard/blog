---
layout: post
title:  "What tech skills companies wants in different places?"
date:   2025-11-21 17:15:14 +0200
categories: jobs  
---

So I'm currently working as a technical consulting company in Sweden, 
and I have been thinking about what skills companies are looking for in different regions.
Im between assignments right now, and I was looking at job postings to see what skills are in demand.

I follow a lot of different tech people on twitter and youtube, and I often see people talking about what skills are in demand in places like San Francisco or Berlin.
But when I look at local job postings there is not really the same demand for skills.

So I assume that others also might be interested in what tech skills are companies asking for in your area.

## Where can you find job postings?

So I don't know about you but if I'm looking for a job I will usually start with talking with friends. But I would also look at linkedIn. 
I don't know what it is like in other countries, but in Sweden, LinkedIn is widely used for job postings. There are also other but I Linkedin is the one I have used besides talking to friends. So I want to collect data from LinkedIn. 

So in order to get some data we need to crawl linkedin job postings.
There is an official API for LinkedIn but it seems as if you need some kind of partnership with them to use it. 

So I looked around at turns out im not the first person trying to scrape linkedin job postings.
I found this [github repository](https://github.com/the-data-circle/linkedin-jobs-webscraping) that grabs job postings from linkedin by looking at network traffic that linkedin generates when you search for jobs. 
The nice thing about this is that we don't need any API key for this. 

## Explore your region 

I have made all of my code public on [github](https://github.com/AxelGard/linkedin-jobs-scrapping) and setup script so that you can easlily run it yourself.
Both as a notebook if you want to play around and as a script to just download the data.

I will collect some more data over time to look at trends over time in my region and some bigger regions.


## What to collect?

So my first thought was to just collect programming languages. 
But I felt that it would be relevant to add frameworks and tools as well.
Since it can give me a feeling for what different tech stacks companies are using.

As an example if we find a job posting that is looking for a "React developer" we infer that they are using JavaScript/TypeScript. 
And since very few job postings are written by a developer it is nice to be bale to implicitly get the programming language or tools being used.

So I have made a CSV with all relevant `skills` that I want to look for in job postings. 
If you are looking at your own region you might want to update the `skills.csv` file in my repository.

Depending on the region the number of job postings can vary a lot.
I have added a parameter that will limit the number of job postings to scrape.
But for bigger regions that means that you will only get a subset of the total job postings.
And linkedin is will also start returning other job postings after a while. 
So the more jobs you request the noise in the data will get bigger. 


### Extracting skills from job postings

Different skills are more or less difficult to extract from job postings. 
Some skills that are easy to extract are programming languages like `Python`, `Java` or `C++`
But some skills are more ambiguous.
For example if we are looking for `C` as a programming language it can be difficult. 

I looked at a bunch of job postings and tried to copy how they are written.
So for example even for a `C++` role it is relatively common to write `C/C++` and `C++`.

When we look at the data this is also something to keep in mind.
That some skills might have been in the job posting but not extracted correctly.
I thought about using a NLP model like Llama or similar, to extract skills from the job posting text.
Then you could do some type of implicit extraction of skills that are not explicitly mentioned in the text.
But that only adds noise to the data in the form of hallucinations from the model.

The way I find the relevant skills is just by doing a simple string search for each skill in the job posting text.
It seems to work fine for the most part.


## Results  

So let's look at some data that I have collected.
This is not all the data I have collected 
but to not make it to long I will so you some of the more interesting findings.

I will also setup a cron job to collect data over time so that we can see trends in the data.
But I will save that for another blog post.

So for all of this I have used the title of `Software Developer` when searching for job postings.

### Sweden

I'm off course mainly interested in Sweden since that is where I live and work.

#### Linköping, Sweden

So I live in Norrköping but most programming jobs are in the nearby city Linköping.
If you don't know Linköping is a university city with a big focus on technology and engineering.
And there is some quite big tech companies located there like SAAB, Qualcomm, Sectra and Ericsson.
This can also be seen in the job postings where the tech stacks that companies are using. 
However, I was only able to find 40 job postings in Linköping when I ran the scraper.

Here are the top 10 technologies that companies are looking for in Linköping:

| Skill	| Number of Job Postings |
|---------------------|------------------------|
| C++	| 14 |
| Python | 14 |
| Git	| 12 |
| C#	| 12 |
| Azure	| 11 |
| Java	| 8 |
| Linux	| 7 |
| Lua	| 7 |
| Kubernetes	| 7 |
| Docker	| 6 |

So this makes sense based on some of the companies that are located in Linköping.
Here is the top 5 companies with the most job postings in Linköping:

| Company name | Number of job postings |
|---------------------|------------------------|
| SAAB	 | 10 |
| Sectra | 	6 |
| Syntronic - A Global Design House | 	5 |
| Professional Galaxy AB | 	2 |
| Voyado | 	2 |

SAAB is a big defense contractor that makes fighter jets and other military equipment.
That is also why I was able to find surprisingly many job postings looking for the Ada developers.
If you don't know about Ada it was basically Rust before Rust was a thing.

Sectra is a medical technology company that makes software for medical imaging there tech stack is mainly in C#.


However it also useful to look at which skills are used by most number of companies. 

| Skill | Number of companies using it |
|---------------------|------------------------|
| C++	| 8 |
| Azure	| 8 |
| Python	| 8 |
| Git	| 8 |
| C#	| 7 |
| Java	| 7 |
| SQL	| 6 |
| Kubernetes	| 6 |
| .NET	| 5 |
| DevOps	| 5 |

So here we can that fore example `SQL` is used at a lot of companies.
Even if it does not place as high if we rank by number of job postings.

However the main languages of ´C++´, ´Python´ being the most used among companies.



#### Stockholm, Sweden

So Stockholm is the capital of Sweden and has a quite big tech scene in general.

Since Stockholm is a much bigger city there are also many more job postings.
I was able to find 312 job postings in Stockholm when I ran the scraper.

Here are the top 10 technologies that companies are looking for in Stockholm:

| Skill	| Number of Job Postings |
| ---------------------|------------------------|
| 	Git	| 129 | 
| 	Java |	99 |
| 	Python |	83 |
| 	AWS |	76 |
| 	CI/CD |	76 |
| 	SQL	| 75 |
| 	React |	71 |
| 	Rust |	68 |
| 	DevOps |	66 |
| 	Azure |	62 |


We can also see how this relates to the companies that are posting jobs in Stockholm:

| Company name | Number of job postings |
|---------------------|------------------------|
| emagine	| 11 |
| Scania Group	| 10 |
| Wolt	| 9 |
| Spotify	| 8 |
| Saab	| 8 |

And then we have the skills most commonly used across companies. 

| Skill | Number of companies using it |
|---------------------|------------------------|
| Git	| 92 |
| Java	| 70 |
| Python	| 61 |
| SQL	| 59 |
| React	| 58 |
| AWS	| 57 |
| CI/CD	| 56 |
| Azure	| 55 |
| DevOps	| 48 |
| Agile	| 47 |

So we see more web development and cloud skills in Stockholm compared to Linköping.

### USA

Let's compare against the USA.

#### San Francisco, USA

Since San Francisco is were all the big tech companies are,
lets compare there posts against my local scene.  
I was able to scrape 359 job postings in SF.

| Skill	| Number of Job Postings |
| ---------------------|------------------------|
|	Python  | 161 |
|	AWS	    | 151 |
|	React	| 144 |
|	TypeScript	| 126 |
|	Rust	| 125 |
|	Java	| 95 |
|	Lua	| 76 |
|	SQL	| 74 |
|	JavaScript	| 72 |
|	Git	| 66 |


And the companies looking for talent is: 

| Company name | Number of job postings |
|---------------------|------------------------|
| OpenAI	 | 25 |
| MLabs	     | 10 |
| Meta	     | 10 |
| Postman	| 5 |
| Google	| 5 |


Here we get all of the big tech companies and there tech stack. 
Comparing this to my local town we can see some simulates, 
but also see that JavaScript is much more in demand in SF. 
We can also see that Stockholm and SF is more similar. 

| Skill | Number of companies using it |
|---------------------|------------------------|
| React	     | 124 |
| Python     | 122 |
| TypeScript | 110 |
| AWS	     | 101 |
| Rust	| 74 |
| Java	| 69 |
| SQL	| 63 |
| Lua	| 62 |
| JavaScript | 56 |
| Ada	| 50 |

Seeing Ada this high in SF seems wried which makes me think that this something else that is being detected. 


## Bias in the data

There is a lot of things one can do to improve the bias in this data. Bigger data set, multiple requests to linkedin.
Requesting from the local region and not just setting it in the request etc. 
The data should be collected over time since different time of year might yield different results. 

There is most likely more skills that need to be added to the search set as well to make it even better.
So you should not really to heavily on this data. 
But when I look at my local data I feel like it is relatively representative for my area at the moment.
I will start collect data over time to see some trends but I still thought this was interesting to share. 


## Conclusion 

For me this means that I will have too look more at `C#` and `Java`,
since I am already very used to work with `C++` and `python`. 

But I hope this was interesting for you as well. 
I will make a new post when or if I find something interesting in trends over time.

Thanks for reading.