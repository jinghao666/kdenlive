Reason: #78 and countless other issues related to serialisation/deserialisation (saving and loading project files in Kdenlive).

Design a new way to save and load projects. It should

* allow unit testing (load example project files and check that they are loaded correctly, upgraded correctly, etc.)
* have a well-defined format (always `.` as decimal point, for example)
* allow easy access to all project information (e.g. Kdenlive properties like timeline ruler position, track/timeline configuration, etc.)
* allow for other serializers (e.g. for MLT)

The current project format (as of 20.04) is an MLT compatible XML file and Kdenlive properties are stored in the kdenlive namespace. When loading the project file, only a few properties are extracted and the rest of the XML DOM is parsed in various places within the application. This leads to difficulties when e.g. dealing with decimal separator issues as it has to be considered in every single place where the DOM is parsed and not just in the deserialiser.