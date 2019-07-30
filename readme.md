<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## Technologies used 

- Laravel5.7
- PHP7.2
- MySql
- bootstrap  "^4.0.0"
- virtualbox
- Vagrant (ship a Vagrantfile with your project, allowing others working on the project on vagrant up)
- By default, vue.js, JQuery and Bootstrap are installed in laravel 5.7
- Voyager Admin Package

## Installation Steps for Setting Up Larael

### 1. Create Laravel Project 

- Install php
  - brew search php
  - brew install php@7.2

- See php version on terminal 
  - php -v

- Install Composer globally:

  - php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
  - php -r "if (hash_file('sha384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  - php composer-setup.php
  - php -r "unlink('composer-setup.php');"
  - mv composer.phar /usr/local/bin/composer
  
  
- Via Composer Create-Project:

  - composer create-project --prefer-dist laravel/laravel ProjectName

- If project has already been created (git clone from github)

  - cd to project root:
    - copy .env.example and create a new fie .env
    - composer install

  - generate application key to .env by running the command:
     - php artisan key:generate

### 2. Add Auth to project
  
  - php artisan make:auth

### 3. Set Up local Dev Env

#### a. Set up local development server
- Start up a local development server with php artisan serve And, visit http://localhost:8000/.
  - php artisan serve 
  
#### b. Aternativly we can set up a robust local development virtual server (already including php and mysql in homestead, skip step 1)

- Install VirtualBox and Vagrant 
  - https://www.virtualbox.org/wiki/Downloads
  - https://www.vagrantup.com/downloads.html
  
- Install The Homestead Vagrant Box
  - vagrant box add laravel/homestead
  
- Go to project root:
  - cd ProjectName
  
- Install Homestead:
  - composer require laravel/homestead --dev 
  
- Generate the Vagrantfile and Homestead.yaml file in your project root:
  - php vendor/bin/homestead make  
  
- Add an /etc/hosts file entry for homestead.test or the domain of your choice.
  - On Mac and Linux, this file is located at /etc/hosts, open it and add the line below(Make sure the IP address listed is the one set in your Homestead.yaml file):
  
    <br> 192.168.10.10  homestead.test
  
- Run vagrant up command in your terminal and access your project at  http://homestead.test in your browser.  
  - vagrant up

- shut down vagrant
  - vagrant destroy --force 




### 4. Activate Bootstrap and Vue.js
- Install Laravel Mix and any depedencies listed in the "devDependencies" section of the package.json file
   - npm install
   
- Run the script by name specified in the "scripts" section of the package.json file
   - for development, run all Mix tasks in webpack.mix.js to run sass to get bootstrap and run js to get vue.js 
     - npm run dev 

   - for production, run all Mix tasks in webpack.mix.js and minify output to run sass to get bootstrap and run js to get vue.js 
     - npm run production //Activate bootstrap and vue.js
   
   - keeping running in terminal and watch all relevant files for changes. Webpack will automatically recompile the assets when it detects a change:
     - npm run watch





## Installation Steps for Adding Voyager Amdin Panel to Larael
(Voyager Laravel Admin & BREAD System (Browse, Read, Edit, Add, & Delete), supporting Laravel 5.4, 5.5, 5.6 and 5.7!)

### 1. Require the Package

After creating your new Laravel application you can include the Voyager package with the following command: 

```bash
composer require tcg/voyager
```

### 2. Add the DB Credentials & APP_URL

Next make sure to create a new database and add your database credentials to your .env file:

```
DB_HOST=localhost
DB_DATABASE=your database name
DB_USERNAME=your database username
DB_PASSWORD=your database password
```

You will also want to update your website URL inside of the `APP_URL` variable inside the .env file:

```
APP_URL=http://localhost:8000
```

> Only if you are on Laravel 5.4 will you need to [Add the Service Provider.](https://voyager.readme.io/docs/adding-the-service-provider)

### 3. Run The Installer

Lastly, we can install voyager. You can do this either with or without dummy data.
The dummy data will include 1 admin account (if no users already exists), 1 demo page, 4 demo posts, 2 categories and 7 settings.

To install Voyager without dummy simply run

```bash
php artisan voyager:install
```

If you prefer installing it with dummy run

```bash
php artisan voyager:install --with-dummy
```

> Troubleshooting: **Specified key was too long error**. If you see this error message you have an outdated version of MySQL, use the following solution: https://laravel-news.com/laravel-5-4-key-too-long-error

And we're all good to go!

Start up a local development server with `php artisan serve` And, visit [http://localhost:8000/admin](http://localhost:8000/admin).

### 4. Creating an Admin User

If you did go ahead with the dummy data, a user should have been created for you with the following login credentials:

>**email:** `admin@admin.com`   
>**password:** `password`

NOTE: Please note that a dummy user is **only** created if there are no current users in your database.

If you did not go with the dummy user, you may wish to assign admin privileges to an existing user.
This can easily be done by running this command:

```bash
php artisan voyager:admin your@email.com
```

If you did not install the dummy data and you wish to create a new admin user you can pass the `--create` flag, like so:

```bash
php artisan voyager:admin your@email.com --create
```

And you will be prompted for the user's name and password.




## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, yet powerful, providing tools needed for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of any modern web application framework, making it a breeze to get started learning the framework.

If you're not in the mood to read, [Laracasts](https://laracasts.com) contains over 1100 video tutorials on a range of topics including Laravel, modern PHP, unit testing, JavaScript, and more. Boost the skill level of yourself and your entire team by digging into our comprehensive video library.



## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

