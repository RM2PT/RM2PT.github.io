---
layout: page
title: InputGen
permalink: /advs/inputGen
---

### Download and Installation

#### Need

InputGen is an advanced feature of **RM2PT**. We recommend you to use InputGen in RM2PT. If you don't have RM2PT, download [here](https://rm2pt.com/downloads/).

#### Installation of InputGen

Open RM2PT, click on `Help` -> `Install New Software`

<img src="../../imgs/InputGen/image-20220507173100117.png" alt="image-20220507173100117" style="zoom: 70%;" />



Type http://rm2pt.com/InputGen-UpdateSite in the Work with field, select RM2Doc and click Next.

<img src="../../imgs/InputGen/1online.png" alt="image-20220507173453144" style="zoom: 50%;" />

**If the update site does not work**, you can choose to install it offline. Click [here](https://github.com/RM2PT/InputGen-UpdateSite/releases/download/v1.0.0/com.rm2pt.generator.inputgen.updatesite-1.0.0-SNAPSHOT.zip) to download InputGen. Follow the steps below to install.

<img src="../../imgs/InputGen/2offline.png" alt="2offline" style="zoom: 50%;" />

<img src="../../imgs/InputGen/3load.png" alt="3load" style="zoom: 50%;" />

<img src="../../imgs/InputGen/4add.png" alt="4add" style="zoom: 50%;" />

<img src="../../imgs/InputGen/5next.png" alt="5next" style="zoom: 50%;" />

选择Install anyway和Restart Now
<img src="../../imgs/InputGen/6installanyway.png" alt="6installanyway" style="zoom: 50%;" />


### Use of InputGen 

#### Need

In order to generate the prototype inputs, you need a requirements model, the **RM2PT project**. For creating or importing a RM2PT project，you can see the tutorial [here](https://rm2pt.com/tutorial/user/create_new_project).

#### First, we use the RM2PT tool to generate a prototype from the requirements model.
After you add a requirements model, first, we use the RM2PT to generate a prototype from the requirements model by right click on `cocome.remodel` -> `RM2PT`-> `OO Prototype`-> ` Generate Desktop Prototype`

<img src="../../imgs/InputGen/10generateprototype.png" alt="10generateprototype" style="zoom: 50%;" />

#### Second, run the InputGen tool to refactor the prototype and update the project.
Second, after you generate a prototype, we use the InputGen to refactor the prototype from the requirements model by right click on `cocome.remodel` -> `RM2PT-dev`-> `InputGen`

<img src="../../imgs/InputGen/9refactor.png" alt="9refactor" style="zoom: 50%;" />

#### The third step is to run the refactored prototype to validate the requirements.
The third step is to run the refactored prototype to validate the requirements by right click on `COCOMEPrototype` -> `pom.xml`-> `run`-> `maven build`
.
<img src="../../imgs/InputGen/8runprototype.png" alt="8runprototype" style="zoom: 50%;" />

#### Before using the prototype to validate the requirements, we can use the Load File button to automatically load the basic data through the external interface, without manually adding it after modeling the administrator.
Before using the prototype to validate the requirements, we can use the Load File button to automatically load the basic data through the external interface, without manually adding it after modeling the administrator. The loaded data is shown in the figure.
<img src="../../imgs/InputGen/11loadfile.png" alt="11loadfile" style="zoom: 50%;" />

#### Now, you can the refactored prototype to validate the requirements.
Now, you can the refactored prototype to validate the requirements.

#### For example,  in the sysytem operation enterItem, InputGen 
For example,in the sysytem operation enterItem,you can choose to click the first input box to generate input data, or click the LoadFromState button to randomly generate input data.
At the same time, if you think that the input data does not meet your own requirements, you can click the InputReset button to reset all inputs and manually input them yourself.

<img src="../../imgs/InputGen/7enterItem.png" alt="7enterItem" style="zoom: 50%;" />


