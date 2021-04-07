# WordPress REST API client for [Dart](https://dart.dev/) | [Flutter](https://flutter.dev)

[![GitHub stars](https://img.shields.io/github/stars/dhmgroup/dart-wp.svg?style=social&label=Star&maxAge=2592000)](https://github.com/dhmgroup/dart-wp/stargazers/)
[![Pub](https://img.shields.io/pub/v/wordpress_api.svg?style=flat-square)](https://pub.dartlang.org/packages/wordpress_api)
[![Build Status](https://travis-ci.org/dhmgroup/dart-wp.svg?branch=master)](https://travis-ci.org/dhmgroup/dart-wp)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/dhmgroup/dart-wp/graphs/commit-activity)

## Description

A WordPress REST API client for dart with support for WooCommerce and custom namespaces/endpoints.

## Features

- Retrieve data from standard WordPress endpoints.
- Retrieve data from any custom namespace

## Installation

In the `dependencies:` section of your `pubspec.yaml`, add the following line:

```yaml
dependencies:
  wordpress_api: <latest_version>
```

## Usage

- Import the package

```dart
import 'package:wordpress_api/wordpress_api';
```

- Initialize WPAPI

```dart
  WordPressAPI api = WordPressAPI('wp-site.com');
```

- Retrieve posts from `getPosts`

  - You can fetch a list of posts by simply calling `.getPosts`. More arguments can be passed to further filter the data returned

  ```dart
    void main() async {
      final api = WordPressAPI('wp-site.com');
      final List<Post> posts = await api.getPosts();
      for (final post in posts) {
        print(post.title);
      }
    }
  ```

  - As of `v3.0`, you can query a single post from the same endpoint by passing an `id`

    ```dart
    void main() async {
      final api = WordPressAPI('wp-site.com');
      final Post posts = await api.getPosts(id: 1);
      print(post.title);
    }
  ```

- Retrieve data from a custom endpoint

```dart
  void main() async {
    final api = WordPressAPI('wp-site.com');
    final WPResponse res = await api.getAsyc(endpoint: 'your-custom-endpoint');
    print(res.data);
  }
```

## ToDo

- Support for `WP Job Manager`.
- Authentication using `Application Passwords`. *WordPress 5.6+ only*
- Fully integrated WooCommerce support.
- Full CRUD operations.
- Support for other popular WordPress Plugins.

Contributions are welcome, report any issues [here](https://github.com/dhmgroup/dart-wp/issues)

## Special Thanks

- [WordPress REST API Handbook](https://developer.wordpress.org/rest-api/reference/) - Read the Handbank for additional arguments/query parameter.


