# CLEAR-SKY DETECTION METHODOLOGY LIBRARY

## What is a clear-sky detection methodolog?
A clear-sky detection (CSD) methodology is one that analysies time-series of irradiance data and determines one of two things, (1) whether or not the sky at the time of measurement was free of clouds, or (2) whether or not there was a clear line of sight to the sun at the time of measurement.

## INTRODUCTION
Welcome to the CSD methodology library. 
This is a collection of as many CSD methodologies as was found in literature and subsequently coded into Matlab. 
Note that many of the models required some form of interpretation or conversion. 
Each model (found in the 'models' directory) state the citation of the literature article or conference proceedings from where the model was interpretted. 
In case that the methdology was provided in code, the disclaimer reads "Coded and Converted by..." as opposed to just "Coded by...".

Whilst the CSD methodologies from literature do state their express intentions between type (1) and type (2) methodologies, our investigation determines that they are often not adept at their intended use case.
As such, it is recommended to consider the different methodologies (start by using the Example.m script) in order to get a feel for their strengths and weaknesses. 

## INPUT DATA
The different types of input into each methodology are defined with the assumption that all data is at 1-minute resolution, and that all data is a single column vector, and also that each of the same index across different variables corresponds to the same time-step.
Note that no methodology needs all of these, however, all are needed should one wish to run all methods. The fewest inputs is two, the most is six. Some need clear-sky irradiance, others do not, some it doesn't matter even it if is a poor clear-sky estimate due to optimisation. 

  ghi = Global horizontal irradiance (Wm-2), column vector. 
 
  ghics = Clear-sky global horizontal irradiance (Wm-2), column vector. 

  dni = Direct normal irradiance (Wm-2), column vector.
 
  dnics = Clear-sky direct normal irradiance (Wm-2), column vector. 

  dif = Diffuse horizontal irradiance (Wm-2), column vector. 

  zen = Solar zenith angle (degrees), column vector.

  exth = Horizontal projection of extraterrestrial irradiance (Wm-2), column vector.

  aod = Total aerosol extinction at 550nm (dimensionless), column vector.

  plot_figure = if this variable is defined, a figure is plotted illustrating the outcome of the select CSD method, e.g. 1;
               

## OUTPUT DATA
Each CSD model offers a single output which is of identical dimensions to the input data. Pay particular attention to the fact that 1 indicates cloud/not-clear and 0 indicates clear. This can, of course be swapped. 

  csd = clear-sky detection. a flag of 1 means that clouds were detected  whereas a flag of 0 means that the hour is clear.
       
## EXAMLPE
An example of all the methodologies in action is provided in "Example.m". 
This script should work first time with no inputs and produce a nice figure to see every model's outputs. 
In the "Example.m" script, sample data is provided from Adelaide Airport irradiance station operated by the Bureau of Meteorology, Australa. It is situated at -34.9524 degrees of latitude and 138.5196 degrees of longitude (East of prime meridian) and at an elevation of 2m above sea level. The time stamps are not provided. 
You can use this to decide which is the most suitable method for your needs, as some have better applications than others. For eaxmple, the Zhang model is by far the best at isolating only entirely clear days, something not offered by other models, whereas the Ellis/Reno/Inman are the most conventional in identifying any possible period where it could be considered clear-sky. Each with a variety of inputs and needs. 

## CONTRIBUTORS
The literature review in order to identify all the different methodologies of CSD was carried out by Christian A. Gueymard.
The model interpretation and coding was carried out by Jamie M. Bright with support, proofing and testing by David Lingfors. 
We pay particular thanks to Gueymard, Jose Ruiz-Arias, Yu Xie, Javier Antonanzas, Ben Ellis and Wenqi 'Flora' Zhang for providing coded versions or support for their models. 

## FUTURE
This repositiory will be managed by Jamie M. Bright. Do not hesitate to get in touch should you have new models or corrections to existing ones that you wish to be ammended.     

## USAGE
All models within this library have been interpretted from literature, converted to Matlab from publically available code, or done so with permission of the author.
These methods are freely available to be downloaded and adopted, though check the licenses. A strict requirement for doing so is that any publications that utilise any model in this libaray must cite the original source as stated in each model [1], cite this repository as the location for obtaining the models [2] and furthermore reference the following work [3] which was the purpose for the conception of this library:

[1] Found at the top of the script of each model

[2] Bright, Jamie M. 2018. Clear-sky Detection Library. Github repository, url <https://github.com/JamieMBright/csd-library>.

[3] Gueymard, Christian. A., Bright, Jamie M. and Lingfors, David. 2018. A posterori clear-sky idenfication methods in solar irradiance time series: Review and validation. Solar Energy. In Review.





