---
title: "How to Join Layers: Unifying Geometric and Attribute Information for Insights"
type: docs
url: /net/how-to-join-layers
weight: 70
---

## Summary

In GIS, joins are a powerful mechanism for combining information from different layers based on a common attribute or spatial relationship. Joins allow you to merge attribute data from one layer (the source layer) with another layer (the target layer) using a common field or a spatial location. The first one is data joining by key (attribute in the table). Using a common field, such as a unique key, you can link records in one table with records in another table. The second approach is data joining by location (spatially). We support both approaches and offer you the opportunity to use them depending on your needs.

Let's suppose you have received data describing the percentage change in population for different districts, and you want to generate several population growth maps based on this information. While your population data is stored in a table in your database and shares a common field with your layer, you can join this data to your geographic objects and utilize additional fields for labeling, categorization, querying, or analyzing layer objects.

Typically, you perform data joins based on a field value that exists in both tables. The field names don't necessarily have to match, but the data types should be the same - numbers with numbers, strings with strings, and so on. You can execute the data join using the "Add Join" geoprocessing tool. When joining attributes, the joined fields are dynamically added to the existing table. Field properties such as aliases, visibility, and number formatting are preserved when adding or removing the join.

## Data merging capabilities

### Data joining by key field

- This approach allows you to **link records from different tables** based on a common key field. You can specify the key field to be used for comparison to establish the relationship between records. This is particularly useful when you need to merge data based on an identifier or another unique attribute.

Specifying the method for comparing data based on the key field:

- You can define **different comparison methods** for the key field when merging data. For example, you can choose to have an exact match, compare based on a pattern, or within a range of values. This allows for more precise determination of relationships between records and gives control over the data merging process.

Specifying a list of attribute names to be merged:

- When merging data, you can specify **specific attributes** that should be merged. This allows you to choose only the necessary attributes for merging and manage the structure of the resulting table.

### Spatial data joining:

- This approach enables you to link data based on their **spatial location**. You can define a search radius within which the nearest geometric objects will be searched for merging. This is useful when you need to join data based on their geographical position.

Controlling the search radius for finding nearest geometric objects:

- You can control **the search radius** when merging data based on location. By specifying a radius value, you determine the distance within which the nearest objects will be searched for merging. This gives control over which objects will participate in the data merging process based on their spatial relationship.

## Demo Project

To better understand the functionality of our library, let's consider [an example of its use](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). This code illustrates how to join vector layers by attributes or geometry.

The provided code consists of two methods, JoinByIndex() and JoinByCoords(), which demonstrate data joining operations using a LayerConstructor class.

In the JoinByIndex() method:

- Lists of geometries with associated attributes are created.

- A LayerConstructor object is initialized.

- The method creates a vector layer and a geometry layer using the provided geometries.

- The geometry layer is joined based on a unique identifier ("Id") using the JoinLayersById() method.

- The resulting joined vector layer is returned.

In the JoinByCoords() method:

- Lists of geometries with associated attributes are created.

- A LayerConstructor object is initialized.

- Geometry layers are created using the provided geometries.

- The geometry layers are joined based on matching coordinates using the JoinLayersByCoords() method.

- The resulting joined vector layer is returned.

In summary, these methods showcase two different approaches to joining data: one based on a unique identifier and the other based on matching coordinates. The LayerConstructor class facilitates these data joining operations.

## Join Options for Index

The JoinOptions class provides a set of options for configuring layers joining. Let's dive deeper into each option:

- **JoinAttributeName**: This option allows you to specify the attribute name from the joined layer whose value will be used in the condition comparison. It establishes the connection between the two layers based on this attribute.

- **TargetAttributeName**: With this option, you can specify the attribute name from the main layer that will be compared to the attribute from the joined layer. It helps determine the matching features between the layers.

- **JoinAttributeNames**: This option enables you to specify a list of attribute names that you want to join. If this list is left empty or set to null, all attributes from the joined layer will be included in the join operation. However, by selecting specific attribute names, you can control the attributes that are joined, which can be useful for optimizing memory usage and processing time.

- **ConditionComparer**: This option allows you to define a custom logic for comparing attribute values between the features of the two layers. By default, it uses the EqualityComparer<object>.Default comparer, which checks for equality. However, you can provide your own custom comparer that implements IEqualityComparer for more specialized comparison requirements.

- **JoinedAttributesPrefix**: This option lets you specify a prefix string for the attribute names of the joined layer. The default value is "joined_", which means that joined attributes will be prefixed with "joined_" in the resulting joined layer. This prefix helps differentiate joined attributes from the original attributes of the main layer.

The JoinOptions class provides flexibility and control over various aspects of the layers joining process. You can specify the attributes to join, customize the comparison logic, and define a prefix for the resulting joined attributes. These options enable you to tailor the joining operation according to your specific needs and achieve meaningful insights from the merged layers.

## Join Options for Geometry

The **JoinByGeometryOptions** class represents options for joining layers based on geometry. Let's explore the functionality of each option:

- **Radius**: This option specifies the radius within which the joined geometry will be searched. It determines the proximity within which features from the main layer will be matched with features from the joined layer based on their spatial relationship.

- **ConditionComparer**: This option allows you to define a custom logic for comparing attribute values from the features of the two layers. By default, it uses the EqualityComparer<object>.Default, which checks for equality. However, you can provide your own custom comparer that implements IEqualityComparer for more specific comparison requirements.

- **JoinedAttributesPrefix**: This option enables you to specify a prefix string for the attribute names of the joined layer. The default value is "joined_", which means that joined attributes will be prefixed with "joined_" in the resulting joined layer. This prefix helps differentiate joined attributes from the original attributes of the main layer.

The JoinByGeometryOptions class provides the means to customize the process of joining layers based on their spatial relationship. By specifying a search radius, you can control the extent within which geometries will be matched. This allows for fine-tuning the joining operation based on the desired proximity between features. The option to provide a custom comparer gives you flexibility in comparing attribute values, and the option to prefix joined attributes helps differentiate them in the resulting joined layer.

Using these options, you can perform spatially aware data merging and obtain insights from the joined layers that are based on their spatial proximity and attribute values.

## Summary

The data joining mechanism in GIS allows for combining geometric objects with their respective attributes from different layers. This provides the ability to analyze and extract information based on spatial and attribute relationships within the data. The options available enable customization of the joining process to meet specific requirements and analysis needs in GIS data.

Data joining facilitates various tasks, including:

- Finding objects that meet specific spatial criteria, such as identifying all buildings within a 500-meter radius of a specific point.

- Combining geographic data to create a more comprehensive and informative overview of a situation.

- Analyzing attribute values of objects based on specific spatial conditions to identify trends and patterns.

The data joining options allow for precise configuration of the object matching process. These options include selecting the attributes to join, defining custom logic for comparing attribute values, and adding a prefix to the attribute names of the joined data. These options provide flexibility and adaptability to the joining process, catering to specific requirements and the goals of data analysis in GIS.

The data joining mechanism plays a significant role in integrating and analyzing geographic data, yielding a more comprehensive understanding of the spatial and attribute nature of the objects under investigation.
