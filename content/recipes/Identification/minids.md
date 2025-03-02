# Identifier Minting Service with Minid Client

**Authors**: 
  * [Philippe Rocca-Serra](https://orcid.org/orcid.org/0000-0001-9853-5668)
  * [Mike D'Arcy ](http://orcid.org/0000-0003-2280-917X)

**Maintainers**: [Philippe Rocca-Serra](https://orcid.org/orcid.org/0000-0001-9853-5668)

**Version**: 1.0

**License**: [CC0 1.0 Universal (CC0 1.0) Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/deed.en)
<!-- 3. [Capability & Maturity Table](#Capability%20&%20Maturity%20Table) -->
<!-- 4. [FAIRification Objectives, Inputs and Outputs](#FAIRification%20Objectives,%20Inputs%20and%20Outputs) -->
## Table of Contents
1. [Main Objectives](#Main%20Objectives)
2. [Graphical Overview of the FAIRification Recipe Objectives](#Graphical%20Overview%20of%20the%20FAIRification%20Recipe%20Objectives)
3. [Installing the minid 2.0 client](#Installing%20the%20minid%202.0%20client)
4. [Minid Client Configuration](#Minid%20Client%20Configuration)
5. [Minid Client Usage](#Minid%20Client%20Usage)
6. [Authors](#Authors)
7. [License](#License)
---

## Main Objectives

The main purpose of this recipe is:

To create a **persistent**, **globally unique** and **resolvable identifier** using the ***Minid client*** accessing the Minid 2.0 release.

___


## Graphical Overview of the FAIRification Recipe Objectives

<!--  <div><img src="./images/minid-mermaid.png" width="650px" style="padding:1px;border:thin solid black;"/></div>   -->

<div><img src="https://github.com/nih-cfde/the-fair-cookbook/blob/dev/content/recipes/Identification/images/minid-mermaid.png" alt="drawing" style="border:1px solid black;" width="650"  align="top" /></div>  
<!-- <div class="mermaid"  style="padding:1px;border:thin solid black;"> -->
<!-- graph TD; -->
<!--  A([file creation]):::box --> <!-- B(New File):::box  -->
<!--    B --> <!-- C{need for a <br>stable <br>identifier?}:::box -->
<!--    C --> <!-- |Yes| D([invoke MINID minting service]):::box -->
<!--    C --> <!-- |No| E(no findable data):::box1 -->
<!--    D --> <!-- F([hdl:20.500.12633/1HK1DTv1wPt3a]):::box -->

<!--
    classDef box font-family:avenir,font-size:14px,fill:#B30000,stroke:#222,color:#fff,stroke-width:1px
    classDef box1 font-family:avenir,font-size:14px,fill:orange,stroke:#222,color:#fff,stroke-width:1px
    linkStyle 0,1,2,3 stroke:#B30000,stroke-width:1px,color:#B30000,font-family:avenir;
    
</div> -->



<!-- ___

## Capability & Maturity Table

| Capability  | Initial Maturity Level | Final Maturity Level  |
| :------------- | :------------- | :------------- |
| identifier minting | minimal | repeatable |

----

## FAIRification Objectives, Inputs and Outputs

| Actions.Objectives.Tasks  | Input | Output  |
| :------------- | :------------- | :------------- |
| [service invokation](http://edamontology.org/operation_3763)  | [file](http://purl.obolibrary.org/obo/STATO_0000002)  | [guid](http://edamontology.org/data_0976)  |
___ -->



## Installing the minid 2.0 client

This is a prerequisite to be able to call the minid API hosted on a server at the following url [http://minid.bd2k.org/minid](http://minid.bd2k.org/minid)

### installing with pip

```python
pip3 install --pre minid
```

### building from source:

use the dev branch to obtain to source
[minid github repository](https://github.com/fair-research/minid)


## Configuration
-------------

1. Prerequisite: create a minig-config.cfg file
  
  As a convenience you need specify this information in a minid configuration file (`~/.minid/minid-config.cfg`)
  To do so from the command line, issue the following:

```bash
$ mkdir ~/Users/philippe/.minid
$ cd .minid
$ touch minid-config.cfg
```


2. Create a GlobusID account
  
  Before using the API you first need to create a [globus account](https://www.globusid.org/create)
  <!-- <kbd>![](./images/globus/globus-account-create.png)<kbd/> -->

 <!--  <div><img src="./images/globus/globus-account-create.png" width="900px" style="padding:1px;border:thin solid black;"/></div>   -->
<div>
  <img src="https://github.com/nih-cfde/the-fair-cookbook/blob/dev/content/recipes/Identification/images/globus/globus-account-create.png" alt="drawing" style="border:1px solid black;" width="650"  align="top" />
</div> 

  <!-- ![](https://i.imgur.com/B5UbkpF.png) -->


  and validate your email address, as part of the registration process. A unique code will be sent to your email address. You must present this code along with your email address when accessing the API.


3. Accessing minid service from the command line
  
  With the completion of the previous steps, you are now ready to use the minid service. The first thing to do is to invoke to `minid login` command

  
  ```bash
  $ minid login
  ```

  This will open the GlobusID login page. Simply enter your credentials obtained from 2.

<!-- ![](./images/globus/globus-account-login.png) -->
<!-- ![](https://i.imgur.com/2OZFcJa.png) -->
<!-- <div>
<img src="./images/globus/globus-account-login.png" width="900px" style="padding:1px;border:thin solid black;"/>
</div>  -->
<div>
  <img src="https://github.com/nih-cfde/the-fair-cookbook/blob/dev/content/recipes/Identification/images/globus/globus-account-login.png" alt="drawing" style="border:1px solid black;" width="750"  align="top" />
</div> 
  
  followed by:

<!-- ![](./images/globus/globus-account-allow.png) -->
<!-- ![](https://i.imgur.com/avzyAFZ.png) -->
<!-- <div>
<img src="./images/globus/globus-account-allow.png" width="900px" style="padding:1px;border:thin solid black;"/>
</div>  -->
<div>
<img src="https://github.com/nih-cfde/the-fair-cookbook/blob/dev/content/recipes/Identification/images/globus/globus-account-allow.png" width="900px" style="padding:1px;border:thin solid black;"/>
</div>
  
  If all goes well, the following browser screen will be shown:

<!-- ![](./images/globus/globus-account-login-success.png) -->
<!-- ![](https://i.imgur.com/THYPg4E.png) -->
<!-- <div>
<img src="./images/globus/globus-account-login-success.png" width="650px" style="padding:1px;border:thin solid black;"/>
</div>  -->
<div>
<img src="https://github.com/nih-cfde/the-fair-cookbook/blob/dev/content/recipes/Identification/images/globus/globus-account-login-success.png" width="900px" style="padding:1px;border:thin solid black;"/>
</div>
  
  While the terminal will show the following:

  ```bash
  You have been logged in.
  ```

  This means you are now ready to use the minid service from the command line.



## Usage
-----

The CLI supports the following simple operations (Note: the `--test` flag creates names in a test namespace that is removed periodically; remove that flag to create production minids.):

* Check a known minid identifier

```bash
$ minid check hdl:20.500.12633/1HK1DTv1wPt3a
```

if everything is setup correctly, the command will return:

```bash
Minid:               hdl:20.500.12633/1HK1DTv1wPt3a
Title:
Checksums:           e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 (sha256)
Created:
Landing Page:        https://identifiers.fair-research.org/hdl:20.500.12633/1HK1DTv1wPt3a
EZID Landing Page:   https://ezid.cdlib.org/id/hdl:20.500.12633/1HK1DTv1wPt3a
Locations:           http://example.com/foo.txt
```

* Create a new identifier (the `--location` option, if provided, must be at the end).

```bash
$ minid --register [--title <title>] <file_name> [--locations <loc1>..<locN>]
```

* Update metadata about an identifier:

```bash
$ minid --update [--title <title>] [--status <status>] [--obsoleted_by <minid>] [--locations <loc1> <loc2>] <identifier>
```

*  View all minid options:

```bash
$ minid -h
```

Landing pages are accessible via the minid website: [http://minid.bd2k.org/minid/landingpage/\<identifier\>](http://minid.bd2k.org/minid/landingpage/\<identifier\>).


### File Manifest Format
------------------------

Minids can only be assigned to a single file. In order to assign a minid to a collection of files, we recommend using a `BDBag <https://github.com/ini-bdds/bdbag>`_ or the minid file manifest format.

The minid file manifest format is a JSON-based format that enumerates a list of files as JSON objects that have the following attributes:


* length: The length of the file in bytes.

* filename: The filename (or path) relative to the manifest file.

* One or more (only one of each) of the following `algorithm:checksum` key-value pairs:

  * md5:\<md5 hex value\>

  * sha256:\<sha256 hex value\>

  * sha512:\<sha512 hex value\>

* url: the URL to the file.

The manifest may be used to create a minid for a collection of files or alternatively as input to the minid batch-register command.

Below is a sample file manifest configuration file:

```bash
  [
      {
          "length":321,
          "filename":"file1.txt",
          "md5":"5bbf5a52328e7439ae6e719dfe712200",
          "sha256":"2c8b08da5ce60398e1f19af0e5dccc744df274b826abe585eaba68c525434806",
          "url" : "globus://ddb59aef-6d04-11e5-ba46-22000b92c6ec/share/godata/file1.txt"
      },
      {
          "length": 632860,
          "filename": "minid_v0.1_Nov_2015.pdf",
          "sha256": "cacc1abf711425d3c554277a5989df269cefaa906d27f1aaa72205d30224ed5f",
          "url" : "http://bd2k.ini.usc.edu/assets/all-hands-meeting/minid_v0.1_Nov_2015.pdf"
      }
  ]
```

## Conclusions:

Using the `Minid` service, resources can now generate stable, resolvable identifiers for their digitial documents. The `Minid` service thus provides a key component to enable `interoperability` and `reusability` by ensuring digital assets get be looked up using a standard protocol (HTTP request). The service also supports data integrity checks thanks to the native support of checksumming functions, with sha256 being recommended.


___

## References:

1. Madduri R, Chard K, D’Arcy M, Jung SC, Rodriguez A, Sulakhe D, et al. (2019) Reproducible big data science: A case study in continuous FAIRness. PLoS ONE 14(4): e0213013. https://doi.org/10.1371/journal.pone.0213013

2. https://minid.readthedocs.io/en/develop/identifiers.html#minids-vs-handles


