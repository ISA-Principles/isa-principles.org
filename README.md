# ISA: Independent Systems Architecture

_Principles for Microservices_

Find out more about ISA at <https://isa-principles.org>
(generated via GitHub Pages from this repository).

# How to contribute?

#### 1. Fork this repository
#### 2. Make a feature branch on your fork
#### 3. Make your changes
You can setup a local [development environment](https://hub.docker.com/r/starefossen/github-pages/) by running the following command in your locally cloned repository:

```
docker run -v "$PWD":/usr/src/app -p "4000:4000" starefossen/github-pages
```

After that you can look at you changes at: `http://0.0.0.0:4000/`

_Note_: You may need to delete `Gemfile.lock` first, the Docker process will recreate a version it can work with.

#### 4. Commit your changes
_Bonus_: Choose a [good commit message](https://chris.beams.io/posts/git-commit/)

#### 5. Open a pull-request
Provide a good title and describe what you want to change and why.

#### 6. Profit! Thanks for contributing :)

_There is also a more [in depth guide from github](https://guides.github.com/introduction/flow/)._ 
