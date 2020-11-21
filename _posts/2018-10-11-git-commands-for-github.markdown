---
layout: post
title:  "Git Commands (for GitHub)"
date:   2018-10-11
categories: Git GitHub
---

Here are some commands that are needed when contributing (suggesting changes) to a repository in GitHub.

1. Fork the repository  
2. Clone from the forked repository (your repository). The url should be the one you see at the top of your browser.
{% highlight ceylon %}
git clone https://github.com/YourUserName/RepoName.git
{% endhighlight %}

{:start="3"}
3. Go into the cloned directory  
{% highlight ceylon %}
cd RepoName
{% endhighlight %}

{:start="4"}
4. Check whether the remote origin and upstream has already been set  
{% highlight java %}
git remote -v
{% endhighlight %}

{:start="5"}
5. Add your repository as the origin (if not set)  
{% highlight ceylon %}
git remote add origin https://github.com/YourUserName/RepoName.git
{% endhighlight %}

{:start="6"}
6. Add the original repository as the upstream  
{% highlight ceylon %}
git remote add upstream https://github.com/FirstOwnersAccount/RepoName.git
{% endhighlight %}

{:start="7"}
7. Make changes as you wish  

8. After making the changes: add, commit and push them to your repository.  	
{% highlight ruby %}
git add <file_one> <file_two> 
git commit -m "xyz changes, abc updated" 
git push origin master
{% endhighlight %}

{:start="9"}
9. Fetch all the new changes from `https://github.com/FirstOwnersAccount/RepoName.git` which will have changes merged from other members’ repositories as well.  
{% highlight ceylon %}
git fetch upstream
{% endhighlight %}

{:start="10"}
10. Make sure you are in the master branch  
{% highlight ceylon %}
git checkout master
{% endhighlight %}

{:start="11"}
11. Rebase your master branch. This will apply all the changes you made, on top of the existing version of the upstream branch.
{% highlight ceylon %}
git rebase upstream/master
{% endhighlight %}

{:start="12"}
12. Send everything to your GitHub repository
{% highlight ceylon %}
git push origin master
{% endhighlight %}

{:start="13"}
13. Go to GitHub and create a pull request. That’s all.

References : [from stackoverflow][stackoverflow-answer] 

[stackoverflow-answer]: https://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository