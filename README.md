# [Blog](http://moonblade.github.io/blog)

[Blog link](http://moonblade.github.io/blog)

Have wanted to write random blog content for a while now, but if I start a wordpress blog, will just forget about its existence and not be able to find it again.

So the solution I figured would be to create my own blog on Git, so that even if its inactive for a long while, will still be able to find it, since its on Git.

---

Used Jekyll to setup the blog content, but ran into issues. Jekyll serve would work, but trying to make it into a github page wouldn't work at all. Figured out later that the version I was using was for default github page, not repo page. 

So chucked it out the window and instead used a github action to build it on the fly and push to a gh-pages branch to be available in repo github.
