#  Sample Domain
The following is a sample domain for the Edge developer protocol.


## Types
### LoaderId  `string`
Unique loader identifier.

### Timestamp `number`
Number of seconds since epoch.

### Headers `object`
Request / response headers as keys /values of Json object.

### ConnectionType `string`
Loading priority of a resource request.
#### Allowed Values
none, cellular2g, cellular3g, cellular4g, bluetooth, ethernet, wifi, wimax, other.

### Request `object`
HTTP request data.
#### Properties
| Name | | | |
|-|-|-|-|
| typeId `string` | optional, experimental | A big description again | |
| AnotherThing `string` | | A big description that maybe is not useful | Allowed values: x y z  |


## Commands
### enable
Enables network tracking, network events will now be delieved to the client.
#### Parameters
| Name | | | |
|-|-|-|-|
| maxTotalBufferSize `number` | optional, *experimental* | Buffer size in bytes to use when prserving network payloads (XHRs, etc.). | |
| maxResourceBufferSize `string` | optional, *experimental* | Per-resource buffer size in bytes to use when preserving network payloads (XHRs, etc.) |  |

### getResponseBody
Returns content served for the given request.
#### Parameters
| | | | |
|-|-|-|-|
| requestId RequestId | | Identifier of the network request to get content for. | |

#### Returns
| | | |
|-|-|-|
| body `string` | *experimental* | Response body. |
| base64Encoded `boolean` | | True, if content was sent as base64. |

### clearBrowserCache
Clears browser cache.

## Events
### requestWillBeSent
Fired when page is about to send HTTP request.
#### Parameters
| | | |
|-|-|-|
| requestId RequestId | | Request identifier. |
| frameId Page.FrameId | *experimental* | Frame identifier. |
| redirect Response | optional | Redirect response data. |

### loadingFinished
Fired when HTTP request has finished loading.
#### Parameters
| | | |
|-|-|-|
| requestId RequestId | | Request identifier. |
| timestamp Timestamp | | Timestamp. |
| encodedDataLength `number` | | Total number of bytes received for this request. |