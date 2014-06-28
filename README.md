array2xml
=========

Convert PHP array to XML with support for attributes and CDATA

Entire project is based on this [issue](http://stackoverflow.com/questions/99350/passing-php-associative-arrays-to-and-from-xml) responses.

Sample usage (it's just a code from my project):

INPUT:
<pre><code>
$input = array('product' => array(
      '@id' => 7,
      'name' => 'some string',
      'seo' => 'some-string',
      'ean' => '',
      'producer' => array(
          'name' => null,
          'photo' => '1.png'
      )
      'stock' => 123,
      'trackstock' => 0,
      'new' => 0,
      'pricewithoutvat' => 1111,
      'price' => 1366.53,
      'discountpricenetto' => null,
      'discountprice' => null,
      'vatvalue' => 23,
      'currencysymbol' => 'PLN',
      '#description' => '',
      '#longdescription' => '',
      '#shortdescription' => '',
      'category' => array(
          'photo' => '1.png',
          'name' => 'test3',
      )
      'staticattributes' => array(
          'attributegroup' => array(
              1 => array(
                  '@name' => 'attributes group',
                  'attribute' => array(
                      0 => array(
                          'name' => 'second',
                          'description' => '<p>desc2</p>',
                          'file' => '',
                      ),
                      1 => 
                        array
                          'name' => 'third',
                          'description' => '<p>desc3</p>',
                          'file' => '',
                      ),
                  )
              )
          )
      ),
      'attributes' => array(),
      'photos' => array(
          'photo' => array(
              0 => array(
                  '@mainphoto' => '1',
                  '%' => '1.png',
              ),
              1 => array(
                  '@mainphoto' => '0',
                  '%' => '2.png',
              ),
              2 => array(
                  '@mainphoto' => '0',
                  '%' => '3.png',
              )
          )
      )
));
</code></pre>

THE CODE:
<pre><code>
$xml = new ArrayToXML();
print $xml->buildXML($input);
</code></pre>

OUTPUT (XML data):
<pre><code>
<?xml version="1.0" encoding="UTF-8"?>
<data>
<product id="8">
<description><![CDATA[]]></description>
<longdescription><![CDATA[]]></longdescription>
<shortdescription><![CDATA[]]></shortdescription>
<name>some string</name>
<seo>some-string</seo>
<ean></ean>
<producer>
<name></name>
<photo>1.png</photo>
</producer>
<stock>123</stock>
<trackstock>0</trackstock>
<new>0</new>
<pricewithoutvat>1111</pricewithoutvat>
<price>1366.53</price>
<discountpricenetto></discountpricenetto>
<discountprice></discountprice>
<vatvalue>23</vatvalue>
<currencysymbol>PLN</currencysymbol>
<category>
<photo>1.png</photo>
<name>test3</name>
</category>
<staticattributes>
<attributegroup name="attributes group">
<attribute>
<name>second</name>
<description>&lt;p&gt;desc2&lt;/p&gt;</description>
<file></file>
</attribute>
<attribute>
<name>third</name>
<description>&lt;p&gt;desc3&lt;/p&gt;</description>
<file></file>
</attribute>
</attributegroup>
</staticattributes>
<photos>
<photo mainphoto="1">1.png</photo>
<photo mainphoto="0">2.png</photo>
<photo mainphoto="0">3.png</photo>
</photos>
</product>
</data>
</code></pre>
