# Google Summer of Code 2019 Final Report by Sneha Sinha

## Organization - CERN-HSF

## Project - Python Components for the SIMPLE Grid Framework

## Links to my contributions and Highlights
Following are the links to my contributions in three parts:

[1.] In the WLCG's repositiories, my work is documented in merged PRs in the following repositories. This code consists of the work done over all the past phases:

  * [Compiler](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler) <br />
I worked on the processing of input site level schema and wrote a function to validate the input config file based on the schema downloaded by the compiler recursively. I also added a new phase in the compiler to process schemas from all components.
  
  * [Validation Engine](https://github.com/WLCG-Lightweight-Sites/wlcg_lightweight_site_config_validation_engine) <br />
I added validators to check for custom data types and extra constraints according to a specified truth table.

  * [Simple Grid Site Repo](https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo) <br />
I worked on the configurations of base files, and creating defaults file and defined custom data types. I continuously improvised on the simple base schema in all phases for better processing by the compiler.

  * [Infra Validation Engine](https://github.com/WLCG-Lightweight-Sites/simple_grid_infra_validation_engine) <br />
I worked on testinfra and wrote tests for verifying correctness of setup of various component and nodes involved in deployment infrastructure.

[2.] I've completed coding tasks and issues in different sprints, these indicate the different phases of my work: [Sprint 1](https://github.com/orgs/WLCG-Lightweight-Sites/projects/2#column-4705944), [Sprint 2](https://github.com/orgs/WLCG-Lightweight-Sites/projects/3#column-5888982) and [Sprint 3](https://github.com/orgs/WLCG-Lightweight-Sites/projects/4#column-6135088) 

[3.] My Pull Requests are further specified below along with the workflow.

### Highlights of my work 
My work during the contribution period can be divided into the following 4 phases. The first two phases consisted of working on the Simple Grid Compiler, in the third phase I contributed to the Configuration Validation Engine and the final phase was based on Simple Grid Infra Validation Engine. <br>

1. Basic structure
2. Extending and processing the schema 
3. Validators
4. Test infrastructure

In the first phase, after deciding on a schema for the site level configuration file, I worked on the configurations of base files, and creating defaults file which consisted of schema to be used by the compiler. I defined custom data types of the SIMPLE framework for the yamale python package in my PR here: [https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/pull/6](https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/pull/6). This schema was continuously improved for better processing by the compiler in the next phases: [https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/pull/8](https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/pull/8), [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/50](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/50).

These `simple-base-schema`, `simple-base-defaults` and `simple-base-meta-info` yaml files previously defined were downloaded by the compiler with configured parametres: [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/49](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/49). I then wrote a function called `get_final_config` to validate the input config file based on the schema downloaded by the compiler [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/52](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/52). The [get_final_config](https://github.com/snehasi/simple_grid_yaml_compiler/blob/fbfc1fd64a0564760de90ed03477bd09d51dcd84/compiler/processor_config_schemas.py#L98) function checks all parts of the site level config file against the base schema by checking recursively inside each component. I improvised on the `get_final_config_values_for_component()` by making this more versatile so that it can process any level of nested schema. These final config parametres were decided according to the following truth table specified in the [SIMPLE Grid Specification document](https://docs.google.com/document/d/1yp_96UXcwNO49cktnHtT61iNmTO0RgrSQukuNYqACpM/edit#) authored by @maany:

<p align="center">
<img width="507" alt="image" src="https://user-images.githubusercontent.com/22666460/63646478-fbceb200-c702-11e9-8088-cf0d77a5ffc1.png">
</p>

In the second phase, I worked on processing the base schema and schema from lightweight componenents into a single schema file as required by YAMALE validator. This was done by adding a new compiler phase `phase 7` in the Compiler: [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/54](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/54). Phase 7 also includes `lc_schema` files so that each lightweight component can have its own schema, allowing for more flexibility and modularity in the schema.

In the third phase I checked if the compiler works as expected in the issue here: [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/issues/51](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/issues/51). This involved troubleshooting and validating the generated output files to be later used by the config validation engine. I worked on writing validators in the config_validation_engine and wrote validators for [str](https://github.com/WLCG-Lightweight-Sites/wlcg_lightweight_site_config_validation_engine/pull/16), [weblink](https://github.com/WLCG-Lightweight-Sites/wlcg_lightweight_site_config_validation_engine/pull/17) and [range](https://github.com/WLCG-Lightweight-Sites/wlcg_lightweight_site_config_validation_engine/pull/15). 

In the final phase, I worked on test infra. This included writing tests for verifying correctness of setup of various component and nodes involved in deployment infrastructure, and are documented here: [https://github.com/WLCG-Lightweight-Sites/simple_grid_infra_validation_engine/pull/9](https://github.com/WLCG-Lightweight-Sites/simple_grid_infra_validation_engine/pull/9).

I also worked on code quality improvements such as implementing the DRY principle by removing redundant get_* functions and introducing new variables for easier accessibilty of file locations: [https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/39](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/39). During the installation phase for infra validation engine, I did troubleshooting on the puppet dev kit's initialisation script and fixed permission on ssh keys in my PR here: [https://github.com/maany/simple_grid_puppet_dev_kit/pull/4](https://github.com/maany/simple_grid_puppet_dev_kit/pull/4).

Here are also some GSoC coding tasks I completed during the proposal phase:
  - [Added validator for site infrastructure](https://github.com/WLCG-Lightweight-Sites/wlcg_lightweight_site_config_validation_engine/pull/11)
  - [Used TestInfra to validate configurations in the basic_config_master container](https://github.com/snehasi/sgyc_test)
  - [Added test functions for repo_processor](https://github.com/WLCG-Lightweight-Sites/simple_grid_yaml_compiler/pull/35)

## Work Left
- [Schema Builder](https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/issues/5)
- [Further extension of the base-schema to add schema elements for wlcg-specific components](https://github.com/WLCG-Lightweight-Sites/simple_grid_site_repo/issues/7)

## Conclusion
The code contributed by me is a part of the v1.0.0 release of the framework and is already being used at the first WLCG site involved in the project. I have also learned and practiced better code quality standards and principles like DRY while contibuting to the project.

I hope my contributions aid the work of people working in WLCG framework in the future as well. 

## Appreciation
It was an amazing opportunity for me to work with CERN-HSF as a Google Summer of Code student contributor, and I learned a great deal during the project period. 

My mentors Mayank and Maarten, have been very responsive and helpful to my questions while working on the project. Their well planned approach to assign me tasks from diffferent aspects of the project, and discussing everything with me has made the coding phase's experience wonderful for me. It has been a wonderful time contributing to this project and working in Open Source. 

Reach me at: 
* Email: ssin9042@gmail.com
* GitHub: [snehasi](https://github.com/snehasi)
* CERN Mattermost uname: snsinha
