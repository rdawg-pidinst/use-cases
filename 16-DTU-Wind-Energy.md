# Technical University of Denmark Wind Energy Department (DTU Wind Energy) Use Case

[Nikola Vasiljevic](https://orcid.org/0000-0002-9381-9693) (niva@dtu.dk), Andrea Vignaroli (andv@dtu.dk) and Jesper Juul Holm (jjho@dtu.dk)

June 2020

## Introduction
The main focus of wind energy domain is to provide practical solutions that will result in cost-effective electricity produced from the wind.
To achive such goals, wind energy domain, even though largely seen as an engineering domain, is characterized as  multi-disciplinary domain, re-using existing solutions and contributing with new one in the following domains:
- Earth Sciences, especially atmospheric science
- Mechanical Engineering
- Material Science
- Electrical Engineering
- Computer Science
- Social Science

At the heart of the wind energy domain are measurements. Generally speaking, wind energy domain immensely cares about the [metrological](https://en.wikipedia.org/wiki/Metrology) aspects of its instruments since uncertainties of measurands directly translate to for example finances (e.g., the uncertainty of 0.1 m/s in the measured wind speed leads to an estimated saving/loss worth around 10 M£ per year for the 25 year lifetime of a wind farm project) or safety ([failure of wind turbines can be dangerous to people](https://www.youtube.com/watch?v=xwS-FH38Fqg)) .

## About DTU Wind Energy
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) is one of the world most recognized wind energy institute. DTU Wind Energy operates [a number of research and commercial facilities](https://www.vindenergi.dtu.dk/english/test-centers/research-facilities) (some permanent, some mobile) which consists of a large pull of instruments. Certain instruments are off-the-shelf-products, while others DTU Wind Energy either develops or modifies to suit particular needs.

## Motivation for PIDINST implementation

There are several reasons for the PIDINST implementation at [DTU Wind Energy](https://www.vindenergi.dtu.dk/english). First of all, using PIDINST we would be able to interconnect people, data, technical/scientific publications, funding, code, workflows and instruments through PIDs. Therefore, it would be possible to capture a full chain of custody and find/access its interconnected elements through by any of them. Using PIDINST we would be able to adopt and practically implement [FAIR principles](https://www.nature.com/articles/sdata201618) beyond data. PIDINST will improve instrument traceability (PID secures resolvable landing page and through certain attributes we can provide information on for example calibration reports). Especially, PIDINST will significantly improve visibility of staff focused on development, maintenance and installation of instruments, and thus their acknowledgement and credits in scientific community, but as well identify their responsibility.

## Measurements standardization
Since the early 1080s, [DTU Wind Energy](https://www.vindenergi.dtu.dk/english) (until 2012 known as [Risø DTU](https://en.wikipedia.org/wiki/Ris%C3%B8_DTU_National_Laboratory_for_Sustainable_Energy)) has been performing field and in-lab research and commercial measurement campaigns globally.

Commercial measurements followed standards such as [IEC 61400](https://en.wikipedia.org/wiki/IEC_61400), which are typically established in cooperation between research institutes and wind energy industry. An important role in this work is played by [MEASNET](http://www.measnet.com/) (**MEAS**uring **NET**work of Wind Energy Institutes) which works towards harmonization of measuring procedures and 'standards' among wind energy institute to secure that high quality measurements are carried out by them. For example, [IEC 61400-12](https://webstore.iec.ch/publication/26603) establish norms for meterological masts and its instrumentation (e.g., length of booms carrying cup anemometers, etc.). Other standards propose naming of data streams (e.g., [IEC 61400-25](https://en.wikipedia.org/wiki/IEC_61400-25)). In IEC, DTU Wind Energy is leading maintenance of current standards and development of new ones. In MEASNET, DTU Wind Energy has been a long-standing active member.

Measurement standards when comes to the instrumentation are followed in research oriented measurement campaigns too, with exceptions for new instruments which are not yet included in them. In research campaigns we often encounter multi-disciplinarity nature of wind energy domain when comes to naming of data streams. Researchers who are more Earth Science oriented tend to use [Climate Forecast standard names](http://cfconventions.org/standard-names.html). On the other hand, researchers with engineering background tend to use IEC. However, even more often we encounter ad-hoc naming of data streams. Nevertheless, DTU Wind Energy is making [a significant push in adoption of the FAIR data principles](https://zenodo.org/record/3865225), and thus trans-disciplinary harmonization of commercial and research oriented measurements.

## General measurement campaigns workflow

### Commercial campaigns


### Research campaigns


## Internal instrumentation database
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) operates an instrumentation database [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk), which is accessible only for selected DTU Wind Energy staff.

<!-- Current schema -->


## Mapping of internal instrumentation to PIDINST schema