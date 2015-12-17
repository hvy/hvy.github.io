---
layout: post
title: Write Better Code - Searching on GitHub
tags: [Git, GitHub]
---

## Begin With StackOverflow, But Then?
*StackOverflow* helps you solve various kinds of programming problems, but of course, this is not always the case. You need to implement that poorly documented library but the answer isn't there and you can't afford to create a new thread waiting for it. The next stop might be *GitHub*; more precisely its search bar.

## The GitHub Search Bar
GitHub has a powerful *search* tool that let's you **find repositories, pull requests, users, issues and even lines in all of the source code** that's available. All this before the bats get out of hell [[1](#References)].

![GitHubSearchBar](/assets/2015-12-18-searchbar.png)

Let's talk about this search bar. Learning how to properly use it might help you implement that poorly documented library. What's really neat is that you can search directly in the source code of all the repositories to **see how others write their code in the same situation which you might be stuck in**.

### How To Use It
Simply write a code snippet or any free text in the search bar and press <kbd>Enter</kbd>. You need to wrap a multi word query with `"` marks to force an exact word sequence match, e.g. `"if let"` to find binding operations. Write `"import tensorflow"` and then select *Code* as the category and *Python* as the language in the results page to search for files using [TensorFlow](https://www.tensorflow.org), the machine learning framework from Google.

#### Advanced Queries
More sophisticated queries can be composed using a query syntax. Here are some examples.

1. [`stars:>1000`](https://github.com/search?q=stars%3A%3E1000&s=updated&type=Repositories) - Queries for all repositories with more than 1000 stars.
2. [`"import tensorflow"  extension:py`](https://github.com/search?utf8=✓&q=%22import+tensorflow%22++extension%3Apy&type=Code&ref=searchresults) - Queries for all Python scripts that include *import tensorflow*.
3. [`crocodile is:open`](https://github.com/search?utf8=✓&q=crocodile+is%3Aopen) - Queries for all open issues containing the word *crocodile*.
4. [`fullname:"Linus Torvalds" language:C`](https://github.com/search?utf8=✓&q=fullname%3A%22Linus+Torvalds%22+language%3AC&type=Users&ref=searchresults) - Queries for all users named *Linus Torvalds* that work with the language *C*.

For more advanced queries, search for an empty string to get the to [main search page of GitHub](https://github.com/search). You can then create the queries using their advanced search page or view a more comprehensive list of examples. There is also a [help section](https://www.elastic.co/use-cases/github).

### How It Works
There are on average 300 search request per minute to the GitHub servers and the handling of all these are backed by the cloud based RESTful search engine [Elasticsearch](https://www.elastic.co/use-cases/github). They manage the 4 million users and the over 8 million repositories comprising over 2 billion documents that need to be indexed for performance, i.e. short query-request to response time. As soon as a repository is being pushed to, the new data is immediately available for search and thus needs to be indexed. This is done by the 120 GB large 128 shards. For more details on how this is done, please refer to [Elasticsearch's GitHub Page](https://www.elastic.co/use-cases/github) or [this interview](http://exploringelasticsearch.com/github_interview.html#ch-githubinterview) with the GitHub developers discussing the scaling of the data (there is also a link to the recording).

## Links
1. [GitHub Search](https://github.com/search)
2. [GitHub Search Help Menu](https://help.github.com/categories/search/)
3. [Elasticsearch - GitHub](https://www.elastic.co/use-cases/github)

## References
1. [Bat Out Of Hell - *Inf. very fast or sudden*.](http://www.urbandictionary.com/define.php?term=Bat+Out+Of+Hell)
