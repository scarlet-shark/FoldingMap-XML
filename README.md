# FoldingMap-XML

  This is the documentation for Folding Map's xml file format (FmXml).  
  This format is based off of KML and OpenStreetMap.org with some furthur customization.
  
  FmXml includess style information as well as geospatial objects.
  
  General note about units: when using a unit within an FmXml file it should be in metric.  
  Time stamps are in the format: year-mm-ddThh:mm:ssZ format.  Example: 2012-09-06T22:41:24Z

## \<BubblePoint\>

	A visualization object that can visualize two fields of data by changing its color and radius.
	
- Extends Point

## \<ColorRamp\>

	Used for visualizations that have an element which changes color.  The ColorRamp maps values to a color.

### Tag Descriptions:

	<default>
		The default color returned by the ramp if queried for a nonexistent key.  
		
	<pair>
		Holds that hex color value for a given key.  The key can be numeric or a string.

### Example:

	<ColorRamp>
		<default>ff444444</default>		
		<pair key="2">b400fe5f</pair>
		<pair key="3">b400fcd7</pair>
		<pair key="4">b400daff</pair>
		<pair key="5">b40062ff</pair>
		<pair key="6">b40001ff</pair>		
	</ColorRamp>

## \<Coordinates\>

	A tag used by various objects to specify what coordinates that object uses.  The tag content can contain a variaty of formats which cna be intermingled.
	
	Possible formats:
		- Node IDs seperated by spaces
		- Two dimentional coordinates consisting of longitude,latitude pairs, with each pair seperated by spaces.
		- Three dimentional coordinates consisting of longitude,latitude,altitude pairs, with each pair seperated by spaces.
		- Four dimentional coordinates consisting of longitude,latitude,altitude,timestamp pairs, with each pair seperated by spaces.
	
### Example:

	<coordinates>12 -3.025556,58.64749 -3.03,58.60027,3 -122.66198,45.52524,4,2012-09-06T22:41:24Z</coordinates>
	
## \<Data\>

	The Data tag is used by Map Objects to store Key/Value Data.  Each object can only contain one of each key.  If an object had multiple entries for a single key only the last entry is used, the others are discarded.

### Syntax:
	<data>
		<pair key="highway">residential</pair>
		<pair key="speed">80</pair>
	</data>

## \<Document\>

	The parent tag for styles and map objects.
	
### Tag Descriptions:

	<name>
		The map name.
		
	<description>
		The map's description.
		
	<view>
		The coordinate to focus the map when it is first loaded.
		
	<projection>
		The map projection to be used when displaying this map.  
		Currently only supports Mercator.
		
	<nodes>
		The list of all nodes used in this map.
		
	<mapstyle>
		The style used in this map.
		
	<layers>
		One or more layers contained by this map.		

## \<Font\>

### Tag Descriptions:

	<face>
		Optional tag to specify the name of the font to be used.
		
	<family>
		The font family, used to create a font if the face tag is missing or the font cannot be found.
		
	<style>
		The font style, possible values are: bold, italic and plain
		
	<size>
		The size of the font to be used.		

## \<Heatmap\>

	Used to indicate a heatmap layer, these layers are dynamically generated.

## \<IconStyle\>

	Specifies how Points are drawn, usually by drawing an Icon, otherwise by a circle.
	
## \<ImageOverlay\>

	Tag for an image overlayed over a map.
	
## \<LabelStyle\>

	Specified how Labels are to be drawn.
	
### Tag Descriptions:

	<Color>
		The main color of the label text.
		
	<OutlineColor>
		The outline color of the label text.
		
	<Font>
		Information on which font and size should be used for the label text.  
		See the Font Tag for more Information.
	
### Example:

	<labelStyle>
		<color>ffffffff</color>
		<outlineColor>ff3c444b</outlineColor>
		<font>
			<family>SansSerif</family>
			<style>Plain</style>
			<size>10</size>
		</font>
	</labelStyle>

## \<LatLonAltBox\>

	A three dimentional bounding box.

- Extends LatLonBox

### Tag Descriptions:

	<north>
		The north bound of this bounding box.
		
	<south>
		The south bound of this bounding box.
		
	<east>
		The east bound of this bounding box.
	
	<west>
		The west bound of this bounding box.
		
	<minAltitude>
		The lower altitude bounds of this bounding box.
	
	<maxAltitude>
		The upper altitude bounds of this bounding box.
	
	<altitudeMode>
		Possible values are clampToGround, relativeToGround, and absolute.
		
### Example:

	<LatLonAltBox>
		<north>5.156742572784424</north>
		<south>5.222579479217529</south>
		<east>10.593417167663574</east>
		<west>10.464646339416504</west>
		<minAltitude>0.0</minAltitude>
		<maxAltitude>5000.0</maxAltitude>
		<altitudeMode>absolute</altitudeMode>
	</LatLonAltBox>

## \<LatLonBox\>

	A two dimentional bounding box.

### Tag Descriptions:

	<north>
		The north bound of this bounding box.
		
	<south>
		The south bound of this bounding box.
		
	<east>
		The east bound of this bounding box.
	
	<west>
		The west bound of this bounding box.

### Example:

	<LatLonBox>
		<north>5.156742572784424</north>
		<south>5.222579479217529</south>
		<east>10.593417167663574</east>
		<west>10.464646339416504</west>
	</LatLonBox>
		
## \<LinearRing\>

	A linear object that where the start point and end point connect creating a closed line.
	
- Extends LineString

## \<LineString\>

	A linear non-closed object that consists of a string of coordinates and rendered as a Line.

### Tag Descriptions:

	<name>
		The name of this LineString.
		
	<ref>	
		The reference ID for this LineString as a long integer.
		
	<coordinates>
		The list of Coordinates used by this LineString.

### Example:

	<LineString id="Road - City Primary">
		<name>Northwest 3rd Avenue</name>
		<Ref>7974</Ref>
		<coordinates>40508548 1832493063 1392884743 40644438 1392884516 1376370008 567256143</coordinates>
	</LineString>

## \<LineStyle\>

	Describes how to style a LineString.
	
### Tag Descriptions:
		
	<color>
		The fill color of the line.		
		
	<outline>
		An integer value 1 or 0 used decide if the line is outlined.
		1 means the line is outlined.
		0 means the line is not outlined.
	
	<outlineColor>
		The color of the outine.
	
	<scaleWidth>
		Specifies if the LineString should be scaled when zooming.  The default is true.
		
	<selectedFillColor>
		The color to fill the line when selected.	
	
	<selectedOutlineColor>
		The color to draw the outline when selected.
		
	<width>
		The width of the line.		

### Example:

	<LineStyle>
		<width>2.5</width>
		<color>ff45c3ff</color>
		<selectedFillColor>803e3ef3</selectedFillColor>
		<outline>1</outline>
		<outlineColor>ff0f8ed9</outlineColor>
		<selectedOutlineColor>ff0000ff</selectedOutlineColor>
	</LineStyle>

## \<Lod\>

	Lod is an acronym for Level of Detail.  This tag describes the size of an area on the screen needed 
	for that area to be displayed.  

### Tag Descriptions:

	<minLodPixels>
		The minimum number pixels needed for this area to be displayed.  
		A value of -1 indicates this field is to be ignored.
		
	<maxLodPixels>
		The maximum number of pixels that can be displayed for this area.
		A value of -1 indicates this field is to be ignored.
		
	<minFadeExtent>
		Distance over which the map objects associated with this LOD fade, from fully opaque to 
		fully transparent.
	
	<maxFadeExtent>
		Distance over which the map objects associated with this LOD fade, from fully transparent to 
		fully opaque.
		
### Example:

	<Lod>
		<minLodPixels>633.0</minLodPixels>
		<maxLodPixels>100000.0</maxLodPixels>
		<minFadeExtent>0.0</minFadeExtent>
		<maxFadeExtent>0.0</maxFadeExtent>
	</Lod>
		
## \<MultiGeometry\>
	A containor for zero or more vector map objects.  Valid objects are:  Point, LineString, LinearRing, Polygon and 
	MultiGeometry.  
	
### Tag Descriptions:

	<description>
		The description for this object.
		
	<elements>
		Contains the elements that make up this MultiGeometry.
		
	<name>
		The name for this object.
		
	<ref>
		The reference ID for this object.
	
### Example:

	<multiGeometry id="id">
		<ref>2</ref>
		<name>Burnside Bridge</name>
		<description>Burnside Bridge MultiGeometry</description>
		<elements>
			<LineString id="Road - City Primary">
				<name>Burnside Bridge</name>
				<Ref>8004</Ref>
				<coordinates>40723784 1634664284 1328062041</coordinates>
			</LineString>
			<LineString id="Road - City Primary">
				<name>Burnside Bridge</name>
				<Ref>8001</Ref>
				<coordinates>1328062041 1634664269 333451694 1328062042</coordinates>
			</LineString>
		</elements>
	</multiGeometry>

## \<NetworkLayer\>

	A layer with object sourced from a seperate file.  This file can be on the local machine or accessable from a URL.  
	Currently supports CSV, FmXML, GeoJSON, GeoRss, KML and KMZ file formats.

- Extends VectorLayer

### Tag Descriptions:

	<name>
		The network layer's name.
		
	<description>
		This layer's description.
		
	<visibility>
		Visibility options for this layer, see the <visibility> tag description.
		
	<href>
		The location of the source file for this network layer.  The source can be a file on the local computer 
		or a URL.
		
	<refreshInterval>
		How often the data from the source file is reloaded.  This is a float value in seconds.
		
## \<Node\>
	Node are a single geospatial point.  A Node can be multidimensional, using at minimum, a Latitude and Longitude; 
	but also may including altitude and a timestamp.  
	
	- Altitude is mesured in meters above mean sea level.  
	- Latitude is mesured in decimal degrees (-90 to 90).
	- Longitude is measured in decimal degrees (-180 to 180).
	- Timestamp is in year-mm-ddThh:mm:ssZ format.  Example: 2012-09-06T22:41:24Z

	Each node has a refference id so map objects can use it as a componet.  This value is a long integer, and when 
	importing from OpenStreetMaps.org the ID will be the same as the OSM ID.  When importing from other sources, 
	ID will start at 1 and increment from there.
	
	Nodes are defined at the begining of the FmXML file and are inclosed in the parent <Nodes> tag.
	
### Syntax:
	
	<nodes>
		<node id="1">-3.025556,58.64749</node>
		<node id="2">-3.03,58.60027,3</node>
		<node id="3">-122.66198,45.52524,4,2012-09-06T22:41:24Z</node>
	</nodes>

## \<OutlineStyle\>
  OutlineStyle is used to detail how the outlines of Polygons and LineStrings are drawn.

### Tag Descriptions:

    <borderCondition>
      The condition on when to use this OutlineStyle.  For Polygons the condition is the Class or Feature Type 
      of the bordering Polygon sharing a vertex.  For LineStrings this tag is ignored.

    <color>
      The color used to draw this outline.

    <selectedColor>
      The color used to draw this outline when the styled object is selected.

    <strokeStyle>
      The stroke style of the outline.  Current supported options are:

        - Solid
        - Solid-Dashed
        - Dashed
        - Dotted
        - Dash-Dotted

    <width>
      A float value indicating the width to draw the outline.

###  Example:

  	<outlineStyle>
   		<borderCondition>Any</borderCondition>
	  	<color>ffddbfa5</color>
	  	<selectedColor>fff33e3e</selectedColor>
	  	<strokeStyle>Solid</strokeStyle>
	 	<width>1</width>
  	</outlineStyle>

## \<PhotoPoint\>

  A GeoTagged photo displayed as a point on a map.

- Extends Point

### Tag Descriptions:

	<name>
		Object's name.
	
	<ref>
		Object's reference number.
		
	<icon>
		The photo of this PhotoPoint.
		
	<coordinates>
		The coordinate id, or coordinate values.

### Example:

	<PhotoPoint id="Photo">
		<name>Portland Oregon - White Stag sign</name>
		<Ref>3</Ref>
		<icon>
			<href>White_Stag_sign.jpg</href>
		</icon>
		<coordinates>1832493064</coordinates>
	</PhotoPoint>

## \<Point\>

  A simple geographical object consisting of a single coordinate.
	
### Syntax:

	<Point id="Bar">
		<name>Yes and No</name>
		<Ref>4066</Ref>
		<coordinates>1234800640</coordinates>
	</Point>
	
## \<Polygon\>
	
	Polygons are defined by one outer-boundry and zero or more inner-boundaries.  The order of the coordinates does not matter as it does in other formats such as KML.
	
### Tag Descriptions:

	<name>
		The polygon's name.
	
	<description>
		The polygon's description, this tag may be ommitted.
		
	<ref>
		The reference ID as interger.  This is used by visualization elements to reference which object is being user to generate a visualization.
		
	<outerBoundary>
		Defines the outer boundary of the polygon.  There can only be one outer boundary.
		
	<innerBoundary>
		Defines an inner-boundary for the polygon. There can be zero or more of there tags.
		
### Example:

	<Polygon id="River">
		<name>Willamette River</name>
		<description>Polygon Description<description>
		<Ref>34</Ref>
		<outerBoundary>
			<coordinates>1711981595 1323150051 32656162 1323150123 1666247227 1666247228 1323150096 1323150126 1666247263 1666247271 1323150066 1666247294 1666247365 32656336 1323150092 1323150122 1666247497 286766364 1666247493 1666247487 1666247283 1666247225 1666247192 1666247189</coordinates>
		</outerBoundary>
	</Polygon>
	
## \<PolyStyle\>

	Defines a style for a polygon.
	
### Example:

	<PolyStyle>
		<featureType>Land</featureType>
		<color>ff79a287</color>
		<selectedColor>ff79a287</color>
		<colorMode>normal</colorMode>
		<fill>1</fill>
		<outlines>
			<outlineStyle>
				<borderCondition>Any</borderCondition>
				<color>b4444444</color>
				<selectedColor>ff0000ff</selectedColor>
				<strokeStyle>Solid</strokeStyle>
				<width>1.0</width>			
			</outlineStyle>
		</outlines>
	</PolyStyle>
	
## \<Region\>

## \<ScreenOverlay\>

## \<Style\>

	Defines a style that can be applied to vector objects within a given map.  A style is referenced by an id.
	The id is defined as an attribute of the style tag, see below.
	
### Syntax:

	<Style id="ID">

		<IconStyle>...</IconStyle>
  		<LabelStyle>...</LabelStyle>
  		<LineStyle>...</LineStyle>
  		<PolyStyle>...</PolyStyle>
	</Style>	
	
## \<TileLayer\>

	A raster layer for display map tiles.
	
## \<TileSource\>

	Describes the soure for tiles used in a TileLayer.  The source can be a diectory structure, file, or a server 
	address.
	
	The directory structure must be in the form: path/Zoom/X/Y.png  Where Zoom, X and Y are integers.
	File must be a .MbTile file.
	Server address must follow the Zoom/X/Y.png or Y.jpg format.
	
### Syntax:	
	
	<TileSource>
		<href>...</href> 
	</TileSource>
	
## \<VectorLayer\>

### Syntax:

	<VectorLayer>
		<name>New Layer</name>
		<description>Layer Description<description>
		<objects>
			...
		</objects>
	</VectorLayer>

## \<Visibility\>

### Tag Descriptions:

	<maxTileZoom>
		The maximum tile layer zoom level that this layer will be visiable at.
		
	<minTileZoom>
		The minimum tile layer zoom level that this layer will be visible at.
