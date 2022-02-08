# packagecloud cookbook

This cookbook provides a resource for installing <https://packagecloud.io> repositories.

[![Cookbook Version](https://img.shields.io/cookbook/v/packagecloud.svg)](https://supermarket.chef.io/cookbooks/packagecloud)
[![CI State](https://github.com/sous-chefs/vault/workflows/ci/badge.svg)](https://github.com/sous-chefs/vault/actions?query=workflow%3Aci)
[![OpenCollective](https://opencollective.com/sous-chefs/backers/badge.svg)](#backers)
[![OpenCollective](https://opencollective.com/sous-chefs/sponsors/badge.svg)](#sponsors)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://opensource.org/licenses/Apache-2.0)

## Maintainers

This cookbook is maintained by the Sous Chefs. The Sous Chefs are a community of Chef cookbook maintainers working together to maintain important cookbooks. If you’d like to know more please visit [sous-chefs.org](https://sous-chefs.org/) or come chat with us on the Chef Community Slack in [#sous-chefs](https://chefcommunity.slack.com/messages/C2V7B88SF).

## Platforms

The following platforms have been certified with integration tests
using Test Kitchen:

- Debian/Ubuntu
- RHEL/CentOS and derivatives
- Fedora and derivatives

## Requirements

- Chef 15+

## Usage

It is recommended to create a project or organization specific [wrapper cookbook](https://www.chef.io/blog/2013/12/03/doing-wrapper-cookbooks-right/) and add the desired custom resources to the run list of a node. Depending on your environment, you may have multiple roles that use different resources from this cookbook. Adjust any attributes as desired.

Depend on `packagecloud` in `metadata.rb` so that the packagecloud resource will be loaded.

For public repos:

```ruby
packagecloud_repo "computology/packagecloud-cookbook-test-public" do
  type "deb"
end
```

For private repos, you need to supply a `master_token`:

```ruby
packagecloud_repo "computology/packagecloud-cookbook-test-private" do
  type "deb"
  master_token "762748f7ae0bfdb086dd539575bdc8cffdca78c6a9af0db9"
end
```

For packagecloud:enterprise users, add `base_url` to your resource:

```ruby
packagecloud_repo "computology/packagecloud-cookbook-test-private" do
  base_url "https://packages.example.com"
  type "deb"
  master_token "762748f7ae0bfdb086dd539575bdc8cffdca78c6a9af0db9"
end
```

For forcing the os and dist for repository install:

```ruby
packagecloud_repo 'computology/packagecloud-cookbook-test-public' do
  type 'rpm'
  force_os 'rhel'
  force_dist '6.5'
end
```

Valid options for `type` include `deb`, `rpm`, and `gem`.

This cookbook performs checks to determine if a package exists before attempting to install it. To enable proxy support _for these checks_ (not to be confused with proxy support for your package manager of choice), add the following attributes to your cookbook:

```ruby
default['packagecloud']['proxy_host'] = 'myproxy.organization.com'
default['packagecloud']['proxy_port'] = '80'
```

## External Documentation

## Credits

Computology, LLC.

## Contributors

This project exists thanks to all the people who [contribute.](https://opencollective.com/sous-chefs/contributors.svg?width=890&button=false)

### Backers

Thank you to all our backers!

![https://opencollective.com/sous-chefs#backers](https://opencollective.com/sous-chefs/backers.svg?width=600&avatarHeight=40)

### Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website.

![https://opencollective.com/sous-chefs/sponsor/0/website](https://opencollective.com/sous-chefs/sponsor/0/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/1/website](https://opencollective.com/sous-chefs/sponsor/1/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/2/website](https://opencollective.com/sous-chefs/sponsor/2/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/3/website](https://opencollective.com/sous-chefs/sponsor/3/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/4/website](https://opencollective.com/sous-chefs/sponsor/4/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/5/website](https://opencollective.com/sous-chefs/sponsor/5/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/6/website](https://opencollective.com/sous-chefs/sponsor/6/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/7/website](https://opencollective.com/sous-chefs/sponsor/7/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/8/website](https://opencollective.com/sous-chefs/sponsor/8/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/9/website](https://opencollective.com/sous-chefs/sponsor/9/avatar.svg?avatarHeight=100)
