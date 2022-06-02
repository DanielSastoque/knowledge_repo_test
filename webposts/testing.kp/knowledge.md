---
authors:
- jdsastoqueb@correo.udistrital.edu.co
created_at: 2022-06-02 00:00:00
path: webposts/testing
tags:
- knowledge
thumbnail: ''
title: Great expectations
tldr: TLRD just to show GE
updated_at: 2022-06-02 21:35:52.816887
---

<div style="text-align: right;"><img src="https://www.factored.ai/wp-content/uploads/2020/11/Recurso-13.png" width="200"></div>

# Continuous Learning Program: Data Quality with Great Expectations

# Content table

1. [Context](#context)
2. [Prerequisites](#prerequisites)
3. [Learning Objectives](#Learning-objectives)
4. [Content](#content)
5. [Optional content](#optional-content)
6. [Project](#projects)

# Context

# Prerequisites

# Learning objectives
* Install Great Expectations locally
* Use built-in expectations
* Apply expectations over a dataset taken from:
    * File system
    * In memory
    * Relational database
    * Cloud
* Generate data docs for the expectations report
* Trigger post-validation actions like:
    * e-mail
    * slack message
    * 
* Integrate Great Expectations with an orchestator
* Generate expectations using the data profiler
* Create a custom expectation
* Configure metada stores in a place different than the file system (database).

# Content

# Optional content

# Project

## Context

## Scenario

## Instructions
* Install Great Expectations on your local machine [[1](https://docs.greatexpectations.io/docs/guides/setup/installation/local)]
* Download the dataset

> **_Tip:_**  For your first steps, use the helper notebooks (those who appear after you run great_expectations CLI commands). Later you'll be able to understand how and which yaml/json files edit directly.

* Create a data context [[2](https://docs.greatexpectations.io/docs/guides/setup/configuring_data_contexts/how_to_configure_a_new_data_context_with_the_cli)]. Navigate over the generated structure under the `great_expectations/` folder [[3](https://docs.greatexpectations.io/docs/tutorials/getting_started/initialize_a_data_context#:~:text=About%20the%20great_expectations/%20directory%20structure)]. Pay special atention to the `great_expectations.yml` file [[4](https://great-expectations.readthedocs.io/en/0.13.4/reference/spare_parts/data_context_reference.html)]

> **_Tip:_** Use a version control tool (like git) to easly see the changes of your configuration files as you run great expectations commands. For example, to see how the `great_expectations.yml` changes after you add a new datasource.

* Create a datasource [[5](https://docs.greatexpectations.io/docs/tutorials/getting_started/tutorial_connect_to_data)] called: ge_datasource. Configure it to read from the file system using pandas and pointing to the `data/` folder. What have change in the `great_expectations.yml` file?
* Create a suite [[6](https://docs.greatexpectations.io/docs/guides/expectations/how_to_create_and_edit_expectations_based_on_domain_knowledge_without_inspecting_data_directly)] called: simple_suite. Configure it to be a manually created suite and, using the core library [[7](https://greatexpectations.io/expectations/), [8](https://legacy.docs.greatexpectations.io/en/latest/reference/glossary_of_expectations.html)], add the following expectations:
    * `pickup_datetime` and `dropoff_datetime` must be dates with the format: *"%Y-%m-%d %H:%M:%S"*
    * `extra` must be a float between zero and one
    * `passenger_count` can't be null
    * `total_amount` can't be negative
    * `tip_amount` must be less than `total_amount`