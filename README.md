# Health & Design Conferences

An open source list of health and design conferences in the United States.

### Use git to make changes

`cd` into a the directory you want your project to live in. Then, clone the project:

```
git clone git@github.com:health-design-conferences/health-design-conferences.github.io.git
```

Once you've cloned the repo, make the changes you want (see below) and then stage, commit, and push your changes:

```
git add <file you've changed>
git commit -m "these are the changes I've made"
git push origin master
```

Finally, submit a [pull request] to merge your changes into the repo.

### Adding a conference

##### From drafts

In your cloned copy of the repo, first look for the conference you'd like to add in the `_drafts\` folder. If you found it, update the conference information, rename the file by adding the start date to the front of the filename in the format `YYYY-MM-DD-`, move the file from the `_drafts\` folder into the `_posts\` folder, and then run the tag rakefile (see below).

##### Not in drafts

If the conference you want to add is not in the `_drafts\` folder, create a new `md` file in the `_posts\` folder using the following naming convention:

```
YYYY-MM-DD-convention-name.md
```

The date should correspond to the start date of the conference. Next, use the following template to add the conference information your new file:

```
---
layout: conference
title: YOUR CONFERENCE TITLE
conference_url: YOUR CONFERENCE HOMEPAGE
location: YOUR CONFERENCE CITY, STATE
host: YOUR HOST
host_url: YOUR HOSTS HOMEPAGE
start_date: YYYY-MM-DD
end_date: YYYY-MM-DD
cost_information:
  - cost information
  - one per line
tags:
  - your
  - tags
---

INFORMATION ABOUT YOUR CONFERENCE
```

It is important to include the `---` dashes. Save the file and run the tags rakefile (see below).

### Editing a conference

To edit a conference, find the conference file you'd like to edit in the `_posts/` folder and make the changes.

##### Incorrect information

Correct the information.

##### Outdated conference date

If a conference date has passed and will not return the following year, delete the conference (see below). If the next conference date and location has been announced, simply edit the date and location in the post file and rename the file using the new start date. If the date has not yet been set, move the post file from the `_posts\` folder into the `_drafts\` folder and rename the file to remove the date. These drafts will remain until a new date is announced.

### Deleting a conference

To delete a conference, delete its corresponding post file in the `_posts\` directory and run the tags rakefile (see below).

### Tags

If you changed any of the tags either by editing, adding, or deleting a conference,
run the following to update the tag files:

```sh
$ rake tags:generate
```

----
### License

MIT

[pull request]:https://github.com/health-design-conferences/health-design-conferences.github.io/pulls
