---
layout: post
title:  "Nested Tables based on JSON"
date:   2018-05-13
categories: ReactJS Tables Nested javascript CSS
---

This post links to a source code that can present JSON data in nested tables using ReactJS, but styled only with CSS.

Before directly moving on to the code, have a look at the images below to check whether that is what you really need. There are two sections:

Raw Data Patient Table  
![Raw Data Patient Table](/assets/nested-table-raw.png)

Pretty Patient Table  
![Pretty Patient Table](/assets/nested-table-pretty.png)

- Raw Data Patient Table - JSON objects are straight away mapped to a nested table
- Pretty Patient Table - A regular table where the data is taken explicitly mapped from the leaves of the JSON object, and placed under each column (this too is a nested table but … read further. You’ll understand)

This was originally a pre GSoC [task][task] for applicants of [LibreHealth][librehealth]. These tables hold data of “patients”, their “encounters” (interaction with the health care center), and “observations” related to those encounters. Here the words “patients”, “encounters” and “observations” are a set of resources according to the [FHIR][fhir] specifications. The data was taken from [HAPI-FHIR server][hapi-server] and pre-processed using a [Java code][java-code].

Initially it only shows the patients data. Click on a row to display the encounters. Similarly click on an encounter to display the observations.

Source code: [click here][source-code]



[task]:        https://gitlab.com/librehealth/toolkit/lh-toolkit/issues/34#note_59349039
[librehealth]: https://librehealth.io/
[fhir]:        https://www.hl7.org/fhir/overview.html
[hapi-server]: http://hapi.fhir.org
[java-code]:   https://github.com/SuKSW/PatientDataViewer
[source-code]: https://github.com/SuKSW/PatientsEncObs.git