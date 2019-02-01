# DataSheet for E.ON ERC Main Building (0001) #

This data set records measurement data from the operation of a non-residential multi-functional building. The data are published with labels and descriptions of the BUDO key [1](#sources).

The measured data come from the building of the E.ON Energy Research Center (E.ON ERC) of the RWTH Aachen University and are written by an advanced monitoring system and a building automation system [2](#sources).

## Motivation for dataset creation ##

- **Why was the dataset created?** (e.g., were there specific tasks in mind, or a specific gap that needed to be filled?)

    Building energy systems are often incorrectly controlled and therefore unnecessarily consume too much energy. [3](#sources) Especially in non-residential buildings, building automation systems offer the possibility to influence the control.

    Many measurements from buildings are required in order to be able to design control systems correctly. Since there is little public measurement data of thermal energy systems, this publication should help to have a basis for machine learning, simulations and therefore optimization of control systems in thermal energy systems.

    Currently, the data is used to enable machine learning approaches for system recognition, semantic recognition and fault recognition of energy systems (especially thermal).

- **What (other) tasks could the dataset be used for?** (Are there obvious tasks for which it should not be used?)

    These data records reflect the operation of a non-residential building and can therefore be used in many different ways. Most application types for Smart Buildings in the thermal area can be evaluated on this data (Statistical load distribution of thermal systems, regression, simulation models, model predictive control).

- **Has the dataset been used for any tasks already?** (If so, where are the results so others can compare (e.g., links to published papers)?)

    The recorded data is used by the EBC itself to evaluate developed advanced control approaches, simulation models or machine learning algorithms (e.g. fault detection or classification of sensor data). In total, more than 40 publications were produced on the data of the E.ON ERC main building. Results of this work can be found on the institute's website.

- **Who funded the creation of the dataset?** (If there is an associated grant, provide the grant number.)

    This dataset is funded by the BMWi (Federal Ministry of Economics and Energy), the European Union (EU) and E.ON gGmbH.

    BMWi: Contribution numbers 03SBE0006A, 03ET1022A, 03ET1218A, 0350018A, 03ET1485A, 03ET1552B, 03ET1298A.
    EU: Contribution numbers "EU FP7 248537", Horizon 2020 "646125"
    E.ON gGmbH: “Energy Concept for the new E.ON ERC Building”

- **Any other comments?**

## Dataset composition ##

- **How is the data set structured? What are the instances?** (e.g., hardware apparatus/sensor, time series, software program, software interface/API; how were these constructs/measures/methods validated?)

     The dataset includes different time series of five unrelated month. Our instances are time series of every “data point“ in  We use the following definition for the term “data point”: a data point is an information carrier that continuously provides information about a state.

    Each time series represents a “data point“ of one BUDO key in the selected interval. Every datapoint consists of a series of the values of the measured variable (BUDO key) and the associated timestamp.

- **Are relationships between instances made explicit in the data? Are schemas of the technical equipment included? Is there a representation of the schemas as a graph model?** (e.g., hardware apparatus/sensor, technical building equipment, software program, software interface/API; how were these constructs/measures/methods validated?)

    The time series of the individual data points are always related to each other. A time series of an installation that is linked to another installation can only be evaluated for certain applications without considering the linked installation. For example, for use in advanced control systems, viewing the linked time series provides valuable information.

    Since the measurements are threshold-based and constantly recorded and thus form a time series, the individual instances are related in time.
    A threshold-based database only stores data, if the change in the measured value is bigger than a defined boundary.

    Also the different systems (like CHP, heat pump,..) are connected in the system. BUDO keys and datapoints are directly related.

- **How many instances of each type are there? What technical equipment is included?** (e.g. technical equipment: heat pump, air handling unit, heat exchanger, boiler; e.g. for instance types: command, temperature sensors, status, volume flow)
  
    The dataset consists of 765 data points of 31 technical devices and five months. These systems are:
        - Geothermal field (221 data points)
        - Heat pump (181 data points)
        - Glycol chiller (68 data points)
        - Heat exchanger (57 data points)
        - Concrete core activation (CCA) (56 data points)
        - Boiler (29 data points)
        - Combined Heat and Power (CHP) (26 data points)
        - Chiller (8 data points)
    For every month and system there exists a single csv file, in which the described data points are assigned to the systems.

    The types of data points are the following:
        - Command (221 data points)
        - Temperature sensors (189 data points)
        - Status (81 data points)
        - Alarm (65 data points)
        - Volume flow (58 data points)
        - Position (26 data points)

- **What data (static and dynamic) of the instances is available?** (e.g. dimensions, types, measured values)

    Each instance is provided with a BUDO key containing the following components:
        - System
        - Subsystem
        - Subsubsystem
        - Medium/Position
        - Type
        - Function type
    In addition, 40 additional categories can be added to each data point. We added the categories “building“, “room“ and “unit“.

- **What information (static and dynamic) can be given about the system(s) in which the data was recorded?**
    __Geothermal field:__
    The geothermal field consists of 41 probes, each 100 meters deep, located around the E.ON main building. A depth of 100 meters was chosen as otherwise German mining law would apply. Each probe contains a comprehensive measurement infrastructure that measures the temperature and overall volume flow through each probe at different depths.

    __Heat pump:__


    __Glycol chiller:__

    __Heat exchanger:__

    __Concrete core activation:__

    __Boiler:__

    __Combined Heat and Power:__

    __Chiller:__




- **What data does each instance consist of?**
    “Raw” data (e.g., unprocessed text or images)? Features/attributes? Is there a label/target associated with instances? If the instances are related to people, are subpopulations identified (e.g., by age, gender, etc.) and what is their distribution?

    Each instance consists of a timeseries and the corresponding sensor-measurement-data of the BUDO key. The measurements of the sensors contain all variables relevant for the operation of a building. These are recorded at different locations within the technical building equipment of the systems. Measured datapoints can be: temperature, pressure, humidity, volume flow, operating messages, fault messages, electrical power, etc.

    The user should also note that many timestamps for a BUDO key have no entry, because the value for this period has not changed and the threshold based database does not store it.

- **Is everything included or does the data rely on external resources?** (e.g., websites, tweets, datasets) If external resources, a) are there guarantees that they will exist, and remain constant, over time; b) is there an official archival version. Are there licenses, fees or rights associated with any of the data?

    Since the published dataset is based on the BUDO key, the documentation of the structure of the BUDO key is a needed external ressource. The documentation explains to what extent the key describes the individual systems and at which position the corresponding sensor is located.
    The documentation can be found here: [https://github.com/RWTH-EBC/BUDO](https://github.com/RWTH-EBC/BUDO).

- **Are there recommended data splits or evaluation measures?** (e.g., training, development, testing; accuracy/AUC)

    The measurements of the sensors are threshold-based, so the series is time-discrete. To reconstruct the continuous-time signal the "zero-order hold" model is recommended.

- **What experiments were initially run on this dataset?** Have a summary of those results and, if available, provide the link to a paper with more information here.

    Most experiments/simulations were carried out in different projects at the EBC as described in "Who funded the creation of the dataset?". Many works had different goals, since the published dataset serves as a basis for many investigations. The results of these experiments/simulations can be found on the institute's website.

- **Any other comments?**

    The data is published in 60 ".csv" files for every system of the building seperately for five seperated months and temporal resolution. In each file every BUDO key of every system is listed. The data exists as raw-data and in 1- and 15-minutes resolution.

### Data Collection Process ###

- **How was the data collected?** (e.g., hardware apparatus/sensor, manual human curation, software program, software interface/API; how were these constructs/measures/methods validated?)

    The data were recorded by the monitoring and the building automation system of the institute. The measured data is stored threshold-based. The data collection system is described at [2](#sources).

- **Who was involved in the data collection process?** (e.g., students, crowdworkers) How were they compensated? (e.g., how much were crowdworkers paid?

    There are a lot of contributors from the EBC, who helped in installing the monitoring system and in collecting this published data. As these are considerably more than 100 persons who can no longer be named individually, a complete list is not provided. Each person has either received compensation in the form of a salary or worked for his or her student education.

- **Over what time-frame was the data collected?** Does the collection time-frame match the creation time-frame?

    The monitoring system and the building automation system exist since 2012. The published data describes a time span of four seperate months. The months selected had the least system downtime since the start of the systems and represent the operation of the building in every season (winter,spring,summer,autum).

- **How many gaps ore errors are in the data set? How can a user of the dataset recognize them?**

    A gap can be determined by comparing the data points. Since the data is stored on a threshold basis, "gaps" can occur naturally. This may be because the threshold value was too high or the data point has not changed. This occurs, for example, if the associated technical system is not switched on.

- **How was the data associated with each instance acquired?** Was the data directly observable (e.g. sensors, commands), reported by subjects, or indirectly inferred/derived from other data? If the latter two, were they validated/verified and if so how?

    The data was acquired by sensors. The sensors are related to each system. The sensors were validated during commissioning. This was repeated at irregular intervals. In particular, the data points from the monitoring system (data source=MONI) are of high quality.

- **Does the dataset contain all possible instances and when not, what is the population?** Is it, for instance, a sample (not necessarily random) from a larger set of instances? Is the sample representative of the larger set? If not, why not (e.g., to cover a more diverse range of instances)? How does this affect possible uses?

    Since there are only four months and xyz out of 9239 data points included, not all possible instances are contained. The population would be every datapoint of every sensor since the start of the monitoring system. As there are gaps in the data collection, four representative months were selected which, taken as a whole, have the least gaps. Since the totality of the data points is difficult to scan, we have selected only meaningful data points and systems of the energy system.

- **Is there information missing from the dataset and why?** (this does not include intentionally dropped instances; it might include, e.g., redacted text, withheld documents) Is this data missing because it was unavailable?

    The measured data is stored threshold-based. If the measured value doesn't change for a long period of time, the time difference between two stored measurements is also big. This big time difference could also result from system downtimes in which no data is stored. In order to provide as accurate data as possible, an investigation of certain sensitive sensors was carried out in advance in order to be able to exclude system failures to a large extent. Nevertheless, there is the possibility that system downtimes have occurred during this time.

- **Are there any known errors, sources of noise, or redundancies in the data?**

    There are natural noise sources in the measurements of the sensors.

- **Any other comments?**

### Data Preprocessing ###

- **What preprocessing/cleaning was done?** (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values, etc.)

    The following steps were taken to process the data:

    __1. Gathering raw measurement data:__ First the raw measurement data of the sensors is collected.  

    __2. Interpretation of data:__ The raw data are converted into the corresponding units and densities if they are measured e.g. by a 0-10 V data point.

    __3. Storing data in database:__ The measured data is stored threshold-based in a database.

    __4. Eliminating downtimes:__ Months with a lot of downtimes and missing time stamps were manually eliminated from the published data. This was achieved by examining some sensitive sensors, which normally change their value frequently. This made it easy to identify downtimes when there was a long period without change. All times with high downtimes were eliminated.

    __5. Equidistant__ All time series were stored raw, that means threshold based. In addition, we have stored equidistant time series that are available in 1- and 15-minute resolution.

- **Was the “raw” data saved in addition to the preprocessed/cleaned data?** (e.g., to support unanticipated future uses)

    All measurements are stored in a database of the EBC. We deliver the raw data with the data set, but recommend using the equidistant data.

- **Is the preprocessing software available?**

    The published data consists of raw measurement data. Therefore, the usual procedures for the provision of measurement data are necessary (low-pass filter, Hampel filter, ...).

- **Does this dataset collection/processing procedure achieve the motivation for creating the dataset stated in the first section of this datasheet?**

    Since this dataset is logged from a non-residential building it represents a typical operation of these type of buildings. With this data the mentioned motivation can be achieved. Of course there are special situations/months that are not covered by this dataset.

- **What must be considered when processing the time series data?**
    The dataset is as it is. Threshold-based storage does not always make it possible to distinguish between a data failure and a measurement that has not changed. However, this is only very rarely the case in the published data sets. There were undocumented failures of individual systems. Some tests were also carried out with the technical installations, which were abnormal in their behaviour.

- **Any other comments?**

### Dataset Distribution ###

- **How is the dataset distributed?** (e.g., website, API, etc.; does the data have a DOI; is it archived redundantly?)

    The dataset will be published on GitHub. At: https://github.com/RWTH-EBC/JUDO

- **When will the dataset be released/first distributed?** (Is there a canonical paper/reference for this dataset?)

    The first part of the dataset will be published at the ISARC 2019 (36th International Symposium on Automation and Robotics in Construction).

- **What license (if any) is it distributed under?** (Are there any copyrights on the data?)

    BSD 3-Clause License
    For every public and private use of the data set, the copyright holder must be named and for every scientific publication, the paper of the corresponding publication must be quoted.

- **Are there any fees or access/export restrictions?**
    There are no fees or restrictions.

- **Any other comments?**

### Dataset Maintenance ###

- **Who is supporting/hosting/maintaining the dataset?** How does one contact the owner/curator/manager of the dataset (e.g. email address, or other contact info)?

    The dataset is hosted and maintained at the EBC. Comments can be send to **Florian Stinner - FStinner@eonerc.rwth-aachen.de (Maintainer)** or **post_ebc@eonerc.rwth-aachen.de(institutes e-mail)**.

- **Will the dataset be updated?** How often and by whom? How will updates/revisions be documented and communicated (e.g., mailing list, GitHub)? Is there an erratum?

    Yes, other systems and chosen instances will be published.

- **If the dataset becomes obsolete how will this be communicated?**
    Since the dataset is published via GitHub, all necessary information will be published on the platform.

- **Is there a repository to link to any/all papers/systems that use this dataset?**
    Several teams from the Institute for Energy Efficient Buildings and Indoor Climate (EBC) of the E.ON Energy Research Center (E.ON ERC) at RWTH Aachen University are working on the building data of the E.ON ERC main building. The main teams, who work with data from the building, are [Building Automation](<https://www.ebc.eonerc.rwth-aachen.de/cms/E-ON-ERC-EBC/Forschung/Forschungsteams/~mobr/Gebaeudeautomation1/?lidx=1>), [Building Energy Systems](<https://www.ebc.eonerc.rwth-aachen.de/cms/E-ON-ERC-EBC/Forschung/Forschungsteams/~mocn/Gebaeudeenergiesysteme2/?lidx=1>) and [Occupant Behavior and Comfort](<https://www.ebc.eonerc.rwth-aachen.de/cms/E-ON-ERC-EBC/Forschung/Forschungsteams/~mocy/Nutzerverhalten-und-Komfort5/?lidx=1>).

- **If others want to extend/augment/build on this dataset, is there a mechanism for them to do so?** If so, is there a process for tracking/assessing the quality of those contributions. What is the process for communicating/distributing these contributions to users?

    Yes, it is possible. Git offers the possibility to work in different branches or just to download the current state of the data. To do so follow the described workflow on the website.

- **Any other comments?**

### Legal & Ethical Considerations ###

- **If the dataset relates to people (i.e. room data), were they informed about the data collection?**
  
    In this publication there is no relation to people. In the future, room-resolved data will be made available for evaluating the comfort or energy supply of individual rooms. These are made anonymous in such a way that no conclusions can be drawn about an individual person.

- **If it relates to people, were they provided with privacy guarantees?**

    There is no relation to people.

- **Does the dataset comply with the EU General Data Protection Regulation (GDPR)?**

    The dataset does comply with the EU General Data Protection Regulation (GDPR) because according to the current state of the art no conclusions can be drawn about individual persons.

- **Does the dataset contain information that might be considered sensitive or confidential?**
  
    The dataset does not contain confidential information.

- **Does the dataset contain information that might be considered inappropriate or offensive?**

    No. The dataset only consists of measurements from a building.

- **Any other comments?**

### Sources ###

[1]: [BUDO ](<https://github.com/RWTH-EBC/BUDO/tree/master/>)

[2]: [Fütterer et al, 2013, "A multifunctional demonstration bench for advanced control research in buildings—Monitoring, control, and interface system"](<https://ieeexplore.ieee.org/document/6700068>)

[3]: [Waide et al, 2014, "The scope for energy and CO2savings in the EU through the use of building automation technology"](<http://neu.eubac.org/fileadmin/eu.bac/BACS_studies_and_reports/2014.06.13_Waide_ECI_-_Energy_and_CO2_savings_BAT.pdf>)