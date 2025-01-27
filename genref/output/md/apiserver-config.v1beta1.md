---
title: kube-apiserver Configuration (v1beta1)
content_type: tool-reference
package: apiserver.k8s.io/v1beta1
auto_generated: true
---
<p>Package v1beta1 is the v1beta1 version of the API.</p>


## Resource Types 


- [EgressSelectorConfiguration](#apiserver-k8s-io-v1beta1-EgressSelectorConfiguration)
  
    

## `EgressSelectorConfiguration`     {#apiserver-k8s-io-v1beta1-EgressSelectorConfiguration}
    


<p>EgressSelectorConfiguration provides versioned configuration for egress selector clients.</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
<tr><td><code>apiVersion</code><br/>string</td><td><code>apiserver.k8s.io/v1beta1</code></td></tr>
<tr><td><code>kind</code><br/>string</td><td><code>EgressSelectorConfiguration</code></td></tr>
    
  
<tr><td><code>egressSelections</code> <B>[Required]</B><br/>
<a href="#apiserver-k8s-io-v1beta1-EgressSelection"><code>[]EgressSelection</code></a>
</td>
<td>
   <p>connectionServices contains a list of egress selection client configurations</p>
</td>
</tr>
</tbody>
</table>

## `Connection`     {#apiserver-k8s-io-v1beta1-Connection}
    

**Appears in:**

- [EgressSelection](#apiserver-k8s-io-v1beta1-EgressSelection)


<p>Connection provides the configuration for a single egress selection client.</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>proxyProtocol</code> <B>[Required]</B><br/>
<a href="#apiserver-k8s-io-v1beta1-ProtocolType"><code>ProtocolType</code></a>
</td>
<td>
   <p>Protocol is the protocol used to connect from client to the konnectivity server.</p>
</td>
</tr>
<tr><td><code>transport</code><br/>
<a href="#apiserver-k8s-io-v1beta1-Transport"><code>Transport</code></a>
</td>
<td>
   <p>Transport defines the transport configurations we use to dial to the konnectivity server.
This is required if ProxyProtocol is HTTPConnect or GRPC.</p>
</td>
</tr>
</tbody>
</table>

## `EgressSelection`     {#apiserver-k8s-io-v1beta1-EgressSelection}
    

**Appears in:**

- [EgressSelectorConfiguration](#apiserver-k8s-io-v1beta1-EgressSelectorConfiguration)


<p>EgressSelection provides the configuration for a single egress selection client.</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>name</code> <B>[Required]</B><br/>
<code>string</code>
</td>
<td>
   <p>name is the name of the egress selection.
Currently supported values are &quot;controlplane&quot;, &quot;master&quot;, &quot;etcd&quot; and &quot;cluster&quot;
The &quot;master&quot; egress selector is deprecated in favor of &quot;controlplane&quot;</p>
</td>
</tr>
<tr><td><code>connection</code> <B>[Required]</B><br/>
<a href="#apiserver-k8s-io-v1beta1-Connection"><code>Connection</code></a>
</td>
<td>
   <p>connection is the exact information used to configure the egress selection</p>
</td>
</tr>
</tbody>
</table>

## `ProtocolType`     {#apiserver-k8s-io-v1beta1-ProtocolType}
    
(Alias of `string`)

**Appears in:**

- [Connection](#apiserver-k8s-io-v1beta1-Connection)


<p>ProtocolType is a set of valid values for Connection.ProtocolType</p>




## `TCPTransport`     {#apiserver-k8s-io-v1beta1-TCPTransport}
    

**Appears in:**

- [Transport](#apiserver-k8s-io-v1beta1-Transport)


<p>TCPTransport provides the information to connect to konnectivity server via TCP</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>url</code> <B>[Required]</B><br/>
<code>string</code>
</td>
<td>
   <p>URL is the location of the konnectivity server to connect to.
As an example it might be &quot;https://127.0.0.1:8131&quot;</p>
</td>
</tr>
<tr><td><code>tlsConfig</code><br/>
<a href="#apiserver-k8s-io-v1beta1-TLSConfig"><code>TLSConfig</code></a>
</td>
<td>
   <p>TLSConfig is the config needed to use TLS when connecting to konnectivity server</p>
</td>
</tr>
</tbody>
</table>

## `TLSConfig`     {#apiserver-k8s-io-v1beta1-TLSConfig}
    

**Appears in:**

- [TCPTransport](#apiserver-k8s-io-v1beta1-TCPTransport)


<p>TLSConfig provides the authentication information to connect to konnectivity server
Only used with TCPTransport</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>caBundle</code><br/>
<code>string</code>
</td>
<td>
   <p>caBundle is the file location of the CA to be used to determine trust with the konnectivity server.
Must be absent/empty if TCPTransport.URL is prefixed with http://
If absent while TCPTransport.URL is prefixed with https://, default to system trust roots.</p>
</td>
</tr>
<tr><td><code>clientKey</code><br/>
<code>string</code>
</td>
<td>
   <p>clientKey is the file location of the client key to be used in mtls handshakes with the konnectivity server.
Must be absent/empty if TCPTransport.URL is prefixed with http://
Must be configured if TCPTransport.URL is prefixed with https://</p>
</td>
</tr>
<tr><td><code>clientCert</code><br/>
<code>string</code>
</td>
<td>
   <p>clientCert is the file location of the client certificate to be used in mtls handshakes with the konnectivity server.
Must be absent/empty if TCPTransport.URL is prefixed with http://
Must be configured if TCPTransport.URL is prefixed with https://</p>
</td>
</tr>
</tbody>
</table>

## `Transport`     {#apiserver-k8s-io-v1beta1-Transport}
    

**Appears in:**

- [Connection](#apiserver-k8s-io-v1beta1-Connection)


<p>Transport defines the transport configurations we use to dial to the konnectivity server</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>tcp</code><br/>
<a href="#apiserver-k8s-io-v1beta1-TCPTransport"><code>TCPTransport</code></a>
</td>
<td>
   <p>TCP is the TCP configuration for communicating with the konnectivity server via TCP
ProxyProtocol of GRPC is not supported with TCP transport at the moment
Requires at least one of TCP or UDS to be set</p>
</td>
</tr>
<tr><td><code>uds</code><br/>
<a href="#apiserver-k8s-io-v1beta1-UDSTransport"><code>UDSTransport</code></a>
</td>
<td>
   <p>UDS is the UDS configuration for communicating with the konnectivity server via UDS
Requires at least one of TCP or UDS to be set</p>
</td>
</tr>
</tbody>
</table>

## `UDSTransport`     {#apiserver-k8s-io-v1beta1-UDSTransport}
    

**Appears in:**

- [Transport](#apiserver-k8s-io-v1beta1-Transport)


<p>UDSTransport provides the information to connect to konnectivity server via UDS</p>


<table class="table">
<thead><tr><th width="30%">Field</th><th>Description</th></tr></thead>
<tbody>
    
  
<tr><td><code>udsName</code> <B>[Required]</B><br/>
<code>string</code>
</td>
<td>
   <p>UDSName is the name of the unix domain socket to connect to konnectivity server
This does not use a unix:// prefix. (Eg: /etc/srv/kubernetes/konnectivity-server/konnectivity-server.socket)</p>
</td>
</tr>
</tbody>
</table>
  
