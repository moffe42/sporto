SPorto is a minimal SAML 2.0 Service Provider implemented in PHP for use in a hub'n'spoke federation like WAYF.

Core functionallity is:

  * Send a signed AuthnRequest to an IdP - Only one IdP supported
  * Receive and verify a signed SAMLResponse
  * Accept an optional list of IdP entityID's used for scoping

It returns an array of the attributes in the AttributeStatement of the response and the response it self.