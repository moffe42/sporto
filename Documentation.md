> <h1>SPorto - Simple SAML 2.0 Service Provider</h1>

> <h2><a href='#about'>About</a></h2>

> <p>SPorto is a minimal SAML 2.0 Service Provider implemented in PHP for<br>
<blockquote>use in a hub'n'spoke federation like WAYF.</p>
<p>Core functionallity is:</p>
<ul>
<blockquote><li>Send a signed AuthnRequest to an IdP - Only one IdP supported</li>
<li>Receive and verify a signed SAMLResponse</li>
<li>Accept an optional list of IdP entityID's used for scoping</li>
</blockquote></ul>
<p>It returns an array of the attributes in the AttributeStatement<br>
of the response and the response it self.</p></blockquote>


> <h2><a href='#example'>Example</a></h2>

> <p>Configuration for SPorto can be placed in a seperate file or in<br>
<blockquote>the sporto.php file itself to make SPorto self-contained. In the<br>
example below the configuration is placed in a seperate file.</p>
<pre><code>&lt;?php<br>
session_start();<br>
include_once('lib/sporto.php');<br>
include_once('config/sporto_config.php');<br>
if(!isset($_SESSION['SAML'])) {<br>
    try {<br>
        $sporto = new SPorto($sporto_config);<br>
        $_SESSION['SAML'] = $sporto-&gt;authenticate();<br>
    } catch (Exception $e) {<br>
        echo $e-&gt;getMessage();<br>
        exit;<br>
    }<br>
}<br>
</code></pre>
</blockquote>> <h2><a href='#config'>Configuration</a></h2>

> <p>Configuration of SPorto is done by putting the required options<br>
<blockquote>into a simple PHP array.</p>
<p>The following is a list of all options and they are all<br>
required.</p>
<ul>
<blockquote><li>idp_certificate - Certificate from IdP</li>
<li>sso - SingleSignoOnService URL for IdP</li>
<li>private_key - Private key used for signing requests</li>
<li>acs - AssertionConsumerService URL for the SP (SHOULD point to a<br>
script that invokes SPorto)</li>
<li>entityid - entityId for the SP</li>
</blockquote></ul></blockquote>

> <h3><a href='#configexample'>Example configuration</a></h3>

```
$sporto_config = array(
    'idp_certificate' => '...',
    'sso' => '...',
    'private_key' => '...',
    'asc' => '...',
    'entityid' => '...',
);
```
> <h2><a href='#session'>Session management</a></h2>

> <p>SPorto does not contain any session management. It is up to the<br>
<blockquote>containig application to handle this.</blockquote>

