# Variables
PHP = php
COMPOSER = composer
CONSOLE = $(PHP) bin/console

# Symfony common commands

install: # Install project dependencies via Composer
    $(COMPOSER) install

update: # Update project dependencies via Composer
    $(COMPOSER) update

cache-clear: # Clear Symfony cache
    $(CONSOLE) cache:clear

migrate: # Run database migrations
    $(CONSOLE) doctrine:migrations:migrate --no-interaction

migration-blank: # Create a blank migration file
    $(CONSOLE) make:migration --empty

fixtures: # Load fixtures into the database
    $(CONSOLE) doctrine:fixtures:load --no-interaction

test: # Run unit tests
    $(PHP) bin/phpunit

serve: # Start Symfony local server
    $(CONSOLE) server:run

# EasyAdmin

easyadmin: # Generate EasyAdmin dashboard
    $(CONSOLE) make:admin:dashboard

# API Platform

api-doc: # Export API Platform OpenAPI documentation
    $(CONSOLE) api:openapi:export --output=public/openapi.json

# Cleaning

clean: # Remove cache and logs
    rm -rf var/cache/* var/log/*

# List all available commands with their description
help:
    @grep -E '^[a-zA-Z_-]+:.*#' $(MAKEFILE_LIST) | \
        awk 'BEGIN {FS = ":.*#"}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

.PHONY: install update cache-clear migrate migration-blank fixtures test serve easyadmin api-doc clean help