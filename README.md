array2xml
=========

Convert PHP array to XML with support for attributes and CDATA

Entire project is based on this [issue](http://stackoverflow.com/questions/99350/passing-php-associative-arrays-to-and-from-xml) responses.

Sample usage (it's just a code from my project):

THE CODE:
<pre><code>$xml = new ArrayToXML();
print $xml->buildXML($input);
</code></pre>

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
      ),
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
      ),
      'staticattributes' => array(
          'attributegroup' => array(
              1 => array(
                  '@name' => 'attributes group',
                  'attribute' => array(
                      0 => array(
                          'name' => 'second',
                          'description' => 'desc2',
                          'file' => '',
                      ),
                      1 => 
                        array(
                          'name' => 'third',
                          'description' => 'desc3',
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

OUTPUT (XML data):
<pre><code>
&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;data&gt;
    &lt;product id="8"&gt;
        &lt;description&gt;&lt;![CDATA[]]&gt;&lt;/description&gt;
        &lt;longdescription&gt;&lt;![CDATA[]]&gt;&lt;/longdescription&gt;
        &lt;shortdescription&gt;&lt;![CDATA[]]&gt;&lt;/shortdescription&gt;
        &lt;name&gt;some string&lt;/name&gt;
        &lt;seo&gt;some-string&lt;/seo&gt;
        &lt;ean&gt;&lt;/ean&gt;
        &lt;producer&gt;
            &lt;name&gt;&lt;/name&gt;
            &lt;photo&gt;1.png&lt;/photo&gt;
        &lt;/producer&gt;
        &lt;stock&gt;123&lt;/stock&gt;
        &lt;trackstock&gt;0&lt;/trackstock&gt;
        &lt;new&gt;0&lt;/new&gt;
        &lt;pricewithoutvat&gt;1111&lt;/pricewithoutvat&gt;
        &lt;price&gt;1366.53&lt;/price&gt;
        &lt;discountpricenetto&gt;&lt;/discountpricenetto&gt;
        &lt;discountprice&gt;&lt;/discountprice&gt;
        &lt;vatvalue&gt;23&lt;/vatvalue&gt;
        &lt;currencysymbol&gt;PLN&lt;/currencysymbol&gt;
        &lt;category&gt;
            &lt;photo&gt;1.png&lt;/photo&gt;
            &lt;name&gt;test3&lt;/name&gt;
        &lt;/category&gt;
        &lt;staticattributes&gt;
            &lt;attributegroup name="attributes group"&gt;
                &lt;attribute&gt;
                    &lt;name&gt;second&lt;/name&gt;
                        &lt;description&gt;&lt;p&gt;desc2&lt;/p&gt;&lt;/description&gt;
                    &lt;file&gt;&lt;/file&gt;
                &lt;/attribute&gt;
                &lt;attribute&gt;
                    &lt;name&gt;third&lt;/name&gt;
                        &lt;description&gt;&lt;p&gt;desc3&lt;/p&gt;&lt;/description&gt;
                    &lt;file&gt;&lt;/file&gt;
                &lt;/attribute&gt;
            &lt;/attributegroup&gt;
        &lt;/staticattributes&gt;
        &lt;photos&gt;
            &lt;photo mainphoto="1"&gt;1.png&lt;/photo&gt;
            &lt;photo mainphoto="0"&gt;2.png&lt;/photo&gt;
            &lt;photo mainphoto="0"&gt;3.png&lt;/photo&gt;
        &lt;/photos&gt;
    &lt;/product&gt;
&lt;/data&gt;

</code></pre>
