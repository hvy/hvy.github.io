---
layout: post
title: Write Better Code - Searching on GitHub
tags: [Git, GitHub]
---

## Prerequisites
You're somewhat familiar with navigating the GitHub homepage and reading StackOverflow.

## StackOverflow, But Then?
*StackOverflow* helps you solve all kinds of programming problems, but that of course is not always the case. You might need to implement that poorly documented library only to find out that there are just too many issues that are hard to debug, answers can't be found in any forum and you can't afford to create a new thread on StackOverflow waiting for it neither. The next stop could be *GitHub*. More precisely its search bar.

## GitHub Search Bar
GitHub has a powerful *search* tool that let's one **find repositories, pull requests, users, issues and even source code lines**. All this before the bats get out of hell [[1](#references)].

![GitHubSearchBar](/assets/2015-12-18-searchbar.png)

Let's talk about this search bar. Learning how to properly use it might help you implement that poorly documented library. What's really neat is that it allows you to search directly in the source code of all the repositories to **see how others have written their code in a similar situation in which you are stuck in**.

### How To Use It

#### Simple Queries
Simply write a code snippet or any free text in the search bar and press <kbd>Enter</kbd>. You need to wrap a multi word query with `"`s to force an exact word sequence match, e.g. `"if let"` to find binding operations. Write `"import tensorflow"`, followed by <kbd>Enter</kbd> and then select *Code* as the category and *Python* as the language in the results page to search for files using [TensorFlow](https://www.tensorflow.org) for instance, the machine learning framework from Google.

It is as previously mentioned possible to search for repositories given names, pull requests, users and issues as well. Let's look at more examples.

#### Advanced Queries
More sophisticated queries can be composed using a query syntax.

1. [`stars:>1000`](https://github.com/search?q=stars%3A%3E1000&s=updated&type=Repositories) - Queries for all repositories with more than 1000 stars.
2. [`"import tensorflow"  extension:py`](https://github.com/search?utf8=✓&q=%22import+tensorflow%22++extension%3Apy&type=Code&ref=searchresults) - Queries for all Python scripts that include *import tensorflow*.
3. [`NOT "Segmentation fault" is:open`](https://github.com/search?utf8=✓&q=NOT+%22segmentation+fault%22+is%3Aopen) - Queries for all open issues that doesn't contain the words *Segmentation fault*.
4. [`fullname:"Linus Torvalds" language:C`](https://github.com/search?utf8=✓&q=fullname%3A%22Linus+Torvalds%22+language%3AC&type=Users&ref=searchresults) - Queries for all users named *Linus Torvalds* that work with the language *C*.

For more advanced queries, search for an empty string to get the to [main search page of GitHub](https://github.com/search). You can then create the queries using their advanced search page or view a more comprehensive list of examples. There is also a [help section](https://help.github.com/categories/search/) explaining the syntax in detail.

#### Notes
It is worth mentioning that a single query cannot be longer than 256 characters and that it cannot consist of more than 5 logical AND, OR or NOT operators. Also, queries are by default incasesensitive.

### How It Works
There are on average 300 search request per minute to the GitHub servers and the handling of all these are backed by the cloud based RESTful search engine [Elasticsearch](https://www.elastic.co/use-cases/github). They manage the 4 million users and the over 8 million repositories comprising over 2 billion documents that need to be indexed for performance, i.e. short query-request to response time. As soon as a repository is being pushed to, the new data is immediately available for search and thus needs to be indexed. This is done by the 120 GB large 128 shards. For more details on how this is carried out, please refer to [Elasticsearch's GitHub Page](https://www.elastic.co/use-cases/github) or [this interview](http://exploringelasticsearch.com/github_interview.html#ch-githubinterview) with the GitHub developers discussing the scaling of the data and its performance of the system (there is also a [link to the recording](https://soundcloud.com/andrewvc-1/github-interview-edited)).

## Conclusions
While going though trending repositories on GitHub might be a good read, one can use the search tool to find specific pieces of code, querying all of the 2 billion documents that is available on GitHub; it can be used to study libraries or could help you find answers to problems that no Internet forum address. Adding the GitHub search to your box of tools might make you a better coder.

Thanks for reading!

## Links
1. [GitHub Search](https://github.com/search)
2. [GitHub Search Help Menu](https://help.github.com/categories/search/)
3. [Elasticsearch - GitHub](https://www.elastic.co/use-cases/github)

## References
[1] Urban Dictionary - Bat Out Of Hell [http://www.urbandictionary.com/define.php?term=Bat+Out+Of+Hell](http://www.urbandictionary.com/define.php?term=Bat+Out+Of+Hell)
