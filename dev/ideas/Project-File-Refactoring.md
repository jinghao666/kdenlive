Reason: #78 and countless other issues related to serialisation/deserialisation (saving and loading project files in Kdenlive).

Design a new way to save and load projects. It should

* allow unit testing (load example project files and check that they are loaded correctly, upgraded correctly, etc.)
* have a well-defined format (always `.` as decimal point, for example)
* allow updating projects to new versions
* allow easy access to all project information (e.g. Kdenlive properties like timeline ruler position, track/timeline configuration, etc.)
* allow for other serializers (e.g. for MLT)

The current project format (as of 20.04) is an MLT compatible XML file and Kdenlive properties are stored in the kdenlive namespace. When loading the project file, only a few properties are extracted and the rest of the XML DOM is parsed in various places within the application. This leads to difficulties when e.g. dealing with decimal separator issues as it has to be considered in every single place where the DOM is parsed and not just in the deserialiser.

Possibly useful links:

* Serialisation Proxy Pattern https://blog.codefx.org/design/patterns/serialization-proxy-pattern/
* Serialisation Proxy explained for Java https://www.youtube.com/watch?v=V1vQf4qyMXg&feature=youtu.be&t=56m12s
* Random issue with information on Serialisation Proxy and Memento Pattern https://github.com/triplea-game/triplea/issues/814

## Now vs. Future

The way project files are handled currently is hat the serialised form (XML) is the model at the same time. This probably made sense in the early days, but now poses many limitations.

![image](uploads/deca45c6ccf29dc4ae1c61f92f29916e/image.png)

A standard way to load saved projects is to parse it (from whatever format it is) and then create an in-memory representation of it which is very easy to work with for developers. This approach has several advantage besides usability for developers. One is that de-serialisation (loading the project file) is happening in a single place and all issues (like decimal separator, document version updates, validations) are done in that step. Afterwards, the developer does not need to worry about reading XML DOM nodes in order to get a property, but simply access the data model in memory.

![image](uploads/fca9607dd572a66c3dfd90304662ed5f/image.png)

## Proposed changes

### Properties

Define properties explicitly instead of storing them in a QMap (where every value is converted to a string and back). Currently there is `KdenliveDoc::getDocumentProperty(const QString &name, const QString &defaultValue)` which is abused for everything.

Before

```c++
QPoint KdenliveDoc::zoom() const
{
    return QPoint(m_documentProperties.value(QStringLiteral("zoom")).toInt(), m_documentProperties.value(QStringLiteral("verticalzoom")).toInt());
}
```

After

```c++
QPoint KdenliveDoc::zoom() const
{
    return m_zoom;
}
```

This can be done separately from the other changes.
