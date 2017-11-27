#  Sample Domain
The following is a sample domain for the Edge developer protocol.

## Types
### LoaderId 
Unique loader identifier.
<br/>
Type: `string`


### Timestamp
Number of seconds since epoch.
<br/>
Type: `number`

#### Headers
Request / response headers as keys /values of Json object.
<br/>
Type: `object`

#### ConnectionType
Loading priority of a resource request.
<br/>
Type: `string`

##### Allowed Values
none, cellular2g, cellular3g, cellular4g, bluetooth, ethernet, wifi, wimax, other.

### Request
HTTP request data.
Type: `object`

| Properties | | |
|-|-|-|
| typeId <br/> optional, *experimental* | `string` | A big description again |
| anothrThing | `string` <br/> *Allowed values: x y z* | A big description that maybe is not useful. |

## Commands
### enable
Enables network tracking, network events will now be delieved to the client.
| Parameters | | |
|-|-|-|
| maxTotalBufferSize <br/> optional, *experimental* | `number` | | Buffer size in bytes to use when prserving network payloads (XHRs, etc.). |
| maxResourceBufferSize <br/> optional, *experimental* | `string` | Per-resource buffer size in bytes to use when preserving network payloads (XHRs, etc.) |

### getResponseBody
Returns content served for the given request.
| Parameters | | |
|-|-|-|
| requestId | RequestId | Identifier of the network request to get content for. |

| Returns | | |
|-|-|-|
| body <br/> *experimental* | string | Response body. |
| base64Encoded | `boolean` | True, if content was sent as base64. |

### clearBrowserCache
Clears browser cache.

## Events
#### requestWillBeSent
Fired when page is about to send HTTP request.
| Parameters | | |
|-|-|-|
| requestId | RequestId | Request identifier. |
| frameId <br/> *experimental* | Page.FrameId | Frame identifier. |
| redirect <br/> *optional* | Response | Redirect response data. |

#### loadingFinished
Fired when HTTP request has finished loading.
| Parameters | | |
|-|-|-|
| requestId | RequestId | Request identifier. |
| timestamp | Timestamp | Timestamp. |
| encodedDataLength | `number` | Total number of bytes received for this request. |