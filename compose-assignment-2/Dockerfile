# create your custom drupal image here, based of official drupal

FROM drupal

RUN apt-get update && apt-get install -y git \ 
    && rm -rf /var/lib/apt/lists/*
# -y says yes to everything so I don't have to
# \ means if the first command succeeded, then run the next one

WORKDIR /var/www/html/themes
RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git \
    && chown -R www-data:www-data bootstrap
# go to that folder and run command
# --single-branch --depth 1 = just the branch that we want and just the latest commit to not download alll history. Saves time and space
# in docker, commands runs as root. (those files were run as root) chown -R = change owner of all files under dir to new user

WORKDIR /var/www/html
# change back to main dir


