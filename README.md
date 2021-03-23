# Basic Odoo project template used by [docky](https://github.com/akretion/docky)

This repo contains all the basic files needed to create an Odoo project from scratch using the [docky](https://github.com/akretion/docky) and [ak](https://github.com/akretion/ak) command-line tools developed by [Akretion](https://akretion.com).

To start a new Odoo project, you don't need to download this repo anymore :

1. Install [docky](https://github.com/akretion/docky) (version > 7.0.5)
```
pip install docky
# or with pipx : pipx install docky --include-deps
```

2. Create en *empty folder* for your Odoo projet and run `docky init` in it
```
mkdir my-odoo-project
cd my-odoo-project
docky init -b 14.0 # or '-b BRANCH_NUMBER' for other Odoo versions, see 'docky init --help'
```

3. Install [ak](https://github.com/akretion/ak)
```
pip install git+https://github.com/akretion/ak.git@master
```

4. Download the Odoo source code and other external modules specified in the [spec.yaml](odoo/spec.yaml) file using `ak build` from the spec.yaml's folder
```
cd odoo
ak build
```

> [ak](https://github.com/akretion/ak) use the [git-aggregator](https://github.com/acsone/git-aggregator) tool by [Acsone](https://www.acsone.eu/).
> More information on the [git-aggregator](https://github.com/acsone/git-aggregator) repo to understand how to fill the [spec.yaml](odoo/spec.yaml) file.

5. Once all the code is downloaded, go back to your project's root folder and launch `docky run`
```
cd ..
docky run
```

On the first `docky run`, docky will download the Odoo image referenced in the [DockerFile](odoo/Dockerfile) and run your different docker-compose files (basically docker-compose.yml, dev.docker-compose.yml or prod.docker-compose.yml) following the environment's variables registered in your **.env** file generated by the `docky init`.

To reload the Odoo docker image or change environment variables, run `docky build`.

More information on [docky](https://github.com/akretion/docky)
