# Analytics Module

Generic base class to define and wrap (image) analytics modules.

Use the [`analytics-module-template`](https://github.com/maet3608/analytics-module-template) 
to create "Analytics Modules".

Analytics Modules provide a standardised way of encapsulating analytics code
(most commonly machine learning classifiers for image data)
with a flexible but standardized API that supports type checking for 
input and output data (IO types).
 
 
## Specification

The Specification defines the Python API of an Analytics Module.
Every Analytic Module must contain Specification, stored in a file 
named `specification.py`, that defines a `SPEC` constant. 
The Specification describes the semantics and types of input/output parameters,
test data and contains meta information about the module. 

For an example of a Specification see `tests/aurmodule/data/specification.py`,
or the [`analytics-module-template`](https://github.com/maet3608/analytics-module-template). 

The IO types are written as strings with a syntax similar to Mime-types that 
are composed of a main type and sub types.

    'main-type/sub-type/details'

where `sub-type` and <details> are optional. Here a simple example for an
integer type:

    'numeric/int'
    
and here a more complex example, describing a Numpy array of shape (10,20,3)
and dtype unsigned integer:

    'ndarray/uint8/10/20/3'    

Technical details can be found in `aurmodule/iotypes.py`
An overview and additional details can be found in the `README.md` for the 
[`analytics-module-template`](https://github.com/maet3608/analytics-module-template

            
## REST API

The Specification defines the Python API of an Analytics Modules but the
IO types described there are usually not suitable for transport over the Web -
with the exception of primitive types such as strings or integers.

The REST API therefore provides conveniency mappers that convert Web data types
such as URLs or data URLs to Python types. Most importantly, the conversion
of Numpy arrays from URLs to images, or data URLs with images or serialized
Numpy arrays is supported. 

Technical details can be found in `aurmodule/util.py`, specifically the
functions `convert_input()` and `convert_output()` are of interest.

An overview and additional details can be found in the `README.md` for the 
[`analytics-module-template`](https://github.com/maet3608/analytics-module-templatee).
              

