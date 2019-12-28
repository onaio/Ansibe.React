# ansible-react

[![Build Status](http://cicd.onalabs.org/api/badges/onaio/ansible-react/status.svg)](http://cicd.onalabs.org/onaio/ansible-react)

Install and configure react apps.

This is a simple and straight-to-the-point role to install react apps.  it is tested against apps that were created using [create react app](https://github.com/facebook/create-react-app).

We only install and configure:

- node
- yarn
- and of course all the javascript packages that your project uses

`NodeJS` and `yarn` will only be installed on the target server if `react_remote_js_build: yes` which is the case by default. When `react_remote_js_build: no`  the build occurs locally and assumes that you have installed `NodeJS` and `yarn`.

We intentionally consider the installation and configuration of web servers, and other things as out of scope for this role.  Therefore, naturally this role is to be used in a playbook that installs and configures those other things, if you need them.

## Role Variables

Some of the more important variables are briefly described below.  You can see all variables by looking at the `defaults/main.yml` file.

```yml
react_system_user: "react"  # name of the user that will own the django installation
react_node_version: 10.x  # the version of node to install

react_git_url: "https://github.com/onaio/kaznet-frontend.git"  # the git repo of your django app which we are installing
react_git_key:
```

### Custom environment variables

[Create react app](https://github.com/facebook/create-react-app) supports [custom environment variables](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-custom-environment-variables) and this role does too!

You can set custom environment variables by using the `react_app_settings` variable, like so:

```yml
react_app_settings:
    REACT_APP_WEBSITE_NAME: 'Example App'
    SOMETHING_ELSE: "you can put anything here"
```

## Testing

This project comes with a Vagrantfile, this is a fast and easy way to test changes to the role, fire it up with `vagrant up`.

See [vagrant docs](https://docs.vagrantup.com/v2/) for getting setup with vagrant

## License

Apache 2

## Authors

[Ona Engineering](https://ona.io)
