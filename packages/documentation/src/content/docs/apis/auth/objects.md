---
title: Objects
---

<!-- Do not edit this file, it has been automatically generated by docusaurus-graphql-plugin -->

## Access

<p style={{ marginBottom: "0.4em" }}><strong>Implements</strong></p>

- [Model](interfaces#model)

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
id<br />
<a href="scalars#id"><code>ID!</code></a>
</td>
<td>
<p>Access id</p>
</td>
</tr>
<tr>
<td>
identifier<br />
<a href="scalars#string"><code>String</code></a>
</td>
<td>
<p>Payment pointer of a sub-resource (incoming payment, outgoing payment, or quote)</p>
</td>
</tr>
<tr>
<td>
type<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>
<p>Access type (incoming payment, outgoing payment, or quote)</p>
</td>
</tr>
<tr>
<td>
actions<br />
<a href="scalars#string"><code>[String]!</code></a>
</td>
<td>
<p>Access action (create, read, list or complete)</p>
</td>
</tr>
<tr>
<td>
limits<br />
<a href="objects#limitdata"><code>LimitData</code></a>
</td>
<td>
<p>Payment limits</p>
</td>
</tr>
<tr>
<td>
createdAt<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>
<p>Date-time of creation</p>
</td>
</tr>
</tbody>
</table>

## Grant

<p style={{ marginBottom: "0.4em" }}><strong>Implements</strong></p>

- [Model](interfaces#model)

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
id<br />
<a href="scalars#id"><code>ID!</code></a>
</td>
<td>
<p>Grant id</p>
</td>
</tr>
<tr>
<td>
client<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>
<p>Payment pointer of the grantee&#39;s account</p>
</td>
</tr>
<tr>
<td>
access<br />
<a href="objects#access"><code>[Access!]!</code></a>
</td>
<td>
<p>Access details</p>
</td>
</tr>
<tr>
<td>
state<br />
<a href="enums#grantstate"><code>GrantState!</code></a>
</td>
<td>
<p>State of the grant</p>
</td>
</tr>
<tr>
<td>
finalizationReason<br />
<a href="enums#grantfinalization"><code>GrantFinalization</code></a>
</td>
<td>
<p>Reason a grant was finalized</p>
</td>
</tr>
<tr>
<td>
createdAt<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>
<p>Date-time of creation</p>
</td>
</tr>
</tbody>
</table>

## GrantEdge

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
node<br />
<a href="objects#grant"><code>Grant!</code></a>
</td>
<td>

</td>
</tr>
<tr>
<td>
cursor<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>

</td>
</tr>
</tbody>
</table>

## GrantsConnection

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
pageInfo<br />
<a href="objects#pageinfo"><code>PageInfo!</code></a>
</td>
<td>

</td>
</tr>
<tr>
<td>
edges<br />
<a href="objects#grantedge"><code>[GrantEdge!]!</code></a>
</td>
<td>

</td>
</tr>
</tbody>
</table>

## LimitData

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
receiver<br />
<a href="scalars#string"><code>String</code></a>
</td>
<td>
<p>Payment pointer URL of the receiver</p>
</td>
</tr>
<tr>
<td>
sendAmount<br />
<a href="objects#paymentamount"><code>PaymentAmount</code></a>
</td>
<td>
<p>Amount to send</p>
</td>
</tr>
<tr>
<td>
receiveAmount<br />
<a href="objects#paymentamount"><code>PaymentAmount</code></a>
</td>
<td>
<p>Amount to receive</p>
</td>
</tr>
<tr>
<td>
interval<br />
<a href="scalars#string"><code>String</code></a>
</td>
<td>
<p>Interval between payments</p>
</td>
</tr>
</tbody>
</table>

## PageInfo

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
endCursor<br />
<a href="scalars#string"><code>String</code></a>
</td>
<td>
<p>Paginating forwards: the cursor to continue.</p>
</td>
</tr>
<tr>
<td>
hasNextPage<br />
<a href="scalars#boolean"><code>Boolean!</code></a>
</td>
<td>
<p>Paginating forwards: Are there more pages?</p>
</td>
</tr>
<tr>
<td>
hasPreviousPage<br />
<a href="scalars#boolean"><code>Boolean!</code></a>
</td>
<td>
<p>Paginating backwards: Are there more pages?</p>
</td>
</tr>
<tr>
<td>
startCursor<br />
<a href="scalars#string"><code>String</code></a>
</td>
<td>
<p>Paginating backwards: the cursor to continue.</p>
</td>
</tr>
</tbody>
</table>

## PaymentAmount

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
value<br />
<a href="scalars#uint64"><code>UInt64!</code></a>
</td>
<td>

</td>
</tr>
<tr>
<td>
assetCode<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>
<p><a href="https://en.wikipedia.org/wiki/ISO_4217">ISO 4217 currency code</a>, e.g. <code>USD</code></p>
</td>
</tr>
<tr>
<td>
assetScale<br />
<a href="scalars#uint8"><code>UInt8!</code></a>
</td>
<td>
<p>Difference in orders of magnitude between the standard unit of an asset and a corresponding fractional unit</p>
</td>
</tr>
</tbody>
</table>

## RevokeGrantMutationResponse

<p style={{ marginBottom: "0.4em" }}><strong>Implements</strong></p>

- [MutationResponse](interfaces#mutationresponse)

<p style={{ marginBottom: "0.4em" }}><strong>Fields</strong></p>

<table>
<thead><tr><th>Name</th><th>Description</th></tr></thead>
<tbody>
<tr>
<td>
code<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>

</td>
</tr>
<tr>
<td>
success<br />
<a href="scalars#boolean"><code>Boolean!</code></a>
</td>
<td>

</td>
</tr>
<tr>
<td>
message<br />
<a href="scalars#string"><code>String!</code></a>
</td>
<td>

</td>
</tr>
</tbody>
</table>
