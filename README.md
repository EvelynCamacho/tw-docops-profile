# tw-docops-profile
This repository is to transcribe my staffing profile into a Static Website using the technologies learnt during the TW DocOps Workshop 2021.

# Overview
This repository contains the final assignment of the workshop. 

It also contains the Wizeline template to create static sites for your projects. Use it freely!

# Markdown Exercise
This section is to practice Markdown.

## My Description

Evelyn is a physicist with a background in theory and mathematics. She has an MSc in Physics of Complex Systems, with studies in ML and Data Science. She has experience in freelance translation and science communication. She is passionate about languages and speaks English, Spanish, Italian, and French. Her hobby is writing short stories. Her goals are to implement concepts, methodologies, and strategies in conjunction with language and communication abilities to develop projects to help in the creation of information and research. She is interested in documenting projects that involve Data Science.

Selected past work:

- Thesis in Active Matter and Collective Motion.
- Documentation for the personalization project of Discovery Kids as part of Wizeline’s TW team.

When she wakes up, she does the following things in order:

1. Yawn.
2. Blink.

She likes eating the following meals.

| Time          |  Meal                |
| ------------- | --------------------:|
| Morning       |  Apple and tea       |
| Afternoon     |  Meat and vegetables |
| Evening       |     Milk and bread   |

She wrote this piece of code in her free time.

```python
docOps = "Cool course!"
print docOps
```

# Running the GitFlow for Documentation
Follow these steps to include the TW MkDocs template in your project's repository.

1. Clone **the project repository** in your local machine.

2. Clone **the TW DocOps repository** in your local machine using the following command.

```
git clone https://github.com/wizeline/tw-docops.git
```

The name of the folder created in your local machine is `tw-docops`.

3. Copy only the `tw-mkdocs` folder, which is inside the `tw-docops` folder, in your project repository.

4. From the terminal of your local machine, access the `tw-mkdocs` folder that is now inside your project repository.

5. Remove the original git files.

```
rm -rf .git .gitignore
```

6. Go back to the root of your project’s official repository folder.

7. Create the `.gitignore` file and write `.DS_Store` to ignore this file.

8. Add the documentation folder to git.

```
git add .
```

9. Create a new branch.

```
git branch -M docPlatform
```

10. Commit the changes.

```
git commit -m "add tw-mkdocs folder"
```

11. Push your changes to the project’s official repository in Github.

```
git push -u origin docPlatform
```

12. Create a pull request in GitHub.

13. Merge the changes in GitHub.

# Installing MkDocs and Creating the Static Site

## Installation

1. Install docker desktop from https://hub.docker.com/editions/community/docker-ce-desktop-mac

2. Change directory to the `tw-mkdocs` folder.

```
cd path/to/project/tw-mkdocs
```

3. Build the MkDocs image.

Execute the following command in the terminal using the current directory.

```
docker build -t tw-mkdocs-img .
```

4. Serve your local environment.

Execute the following command in the terminal after the docker image creation.

```
docker run --name wizeline-mkdocs-template -p 9090:9090 --volume="$PWD:/app" tw-mkdocs-img:latest
```

> **Note:** Use the `-d` flag in the above command to detach your terminal from the running container.

5. Start working. Open http://localhost:9090 to see all your changes.

6. Add, commit, push, and merge all your changes in the project's repository on GitHub.

## Stop mkdocs

1. Open Docker's dashboard.

2. Locate the wizeline-mkdocs-template container and stop it.

3. Wait until the terminal process stops.

## Restart mkdocs

1. Open docker's dashboard.

2. Locate the wizeline-mkdocs-template container and start it.

## Create static site
1. Create a branch in GitHub named **`gh-pages`**

2. In GitHub Settings, go to the **GitHub Pages** section

3. Configure the **`gh-pages`** branch and the **`/docs`** folder as the source of your GitHub Pages site.

4. From the terminal, change directory to the `tw-mkdocs` folder in your project's repository.

5. Execute the following command in the terminal to fetch the changes in GitHub.

```
git fetch
```

6. Checkout to the **`gh-pages`** branch.

```
git checkout gh-pages
```

7. Execute the following command.

```
docker run --rm --volume="$PWD:/app" -it tw-mkdocs-img:latest mkdocs build && ( cd .. && cp -r tw-mkdocs/site/ docs )
```

8. Add the changes to git.

```
git add ../docs/ site/
```

9. Commit the changes.

```
git commit -m "Create static site folders"
```

10. Push your changes to the project’s official repository in Github.

```
git push origin gh-pages
```

11. From the **`gh-pages`** branch, delete the `README.md` file that is in the root of the project's folder in your local machine. This is to avoid problems with the folder that the static site takes to build.

12. Add the changes to git.

```
git add ../README.md
```

13. Commit the changes.

```
git commit -m "Remove README file"
```

14. Push your changes to the project’s official repository in Github.

```
git push origin gh-pages
```

15. Go to your static site.

**There it is! You made it!**
