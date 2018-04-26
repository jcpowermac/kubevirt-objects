---
title: KubeVirt API v
language_tabs: []
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="KubeVirt-API">KubeVirt API v</h1>

> Scroll down for example requests and responses.

This is KubeVirt API an add-on for Kubernetes.

Email: <a href="mailto:kubevirt-dev@googlegroups.com">kubevirt-dev</a> Web: <a href="https://github.com/kubevirt/kubevirt">kubevirt-dev</a> 
License: <a href="https://www.apache.org/licenses/LICENSE-2.0">Apache 2.0</a>

<h1 id="KubeVirt-API-Default">Default</h1>

## getAPIGroup

<a id="opIdgetAPIGroup"></a>

> Code samples

`GET /apis/subresources.kubevirt.io`

*Get a KubeVirt API Group*

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "name": "string",
  "preferredVersion": {
    "groupVersion": "string",
    "version": "string"
  },
  "serverAddressByClientCIDRs": [
    {
      "clientCIDR": "string",
      "serverAddress": "string"
    }
  ],
  "versions": [
    {
      "groupVersion": "string",
      "version": "string"
    }
  ]
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "name": "string",
  "preferredVersion": {
    "groupVersion": "string",
    "version": "string"
  },
  "serverAddressByClientCIDRs": [
    {
      "clientCIDR": "string",
      "serverAddress": "string"
    }
  ],
  "versions": [
    {
      "groupVersion": "string",
      "version": "string"
    }
  ]
}
```

<h3 id="getAPIGroup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.APIGroup](#schemav1.apigroup)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|default|Default|OK|[v1.APIGroup](#schemav1.apigroup)|

<aside class="success">
This operation does not require authentication
</aside>

## getAPIResources

<a id="opIdgetAPIResources"></a>

> Code samples

`GET /apis/subresources.kubevirt.io/v1alpha1`

*Get a KubeVirt API resources*

> Example responses

```json
{
  "apiVersion": "string",
  "groupVersion": "string",
  "kind": "string",
  "resources": [
    {
      "categories": [
        "string"
      ],
      "group": "string",
      "kind": "string",
      "name": "string",
      "namespaced": true,
      "shortNames": [
        "string"
      ],
      "singularName": "string",
      "verbs": [
        "string"
      ],
      "version": "string"
    }
  ]
}
```

```json
{
  "apiVersion": "string",
  "groupVersion": "string",
  "kind": "string",
  "resources": [
    {
      "categories": [
        "string"
      ],
      "group": "string",
      "kind": "string",
      "name": "string",
      "namespaced": true,
      "shortNames": [
        "string"
      ],
      "singularName": "string",
      "verbs": [
        "string"
      ],
      "version": "string"
    }
  ]
}
```

<h3 id="getAPIResources-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.APIResourceList](#schemav1.apiresourcelist)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|default|Default|OK|[v1.APIResourceList](#schemav1.apiresourcelist)|

<aside class="success">
This operation does not require authentication
</aside>

## checkHealth

<a id="opIdcheckHealth"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/healthz`

*Health endpoint*

<h3 id="checkHealth-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Unhealthy|None|
|default|Default|OK|None|

<aside class="success">
This operation does not require authentication
</aside>

## listNamespacedOfflineVirtualMachine

<a id="opIdlistNamespacedOfflineVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines`

*Get a list of OfflineVirtualMachine objects.*

<h3 id="listNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "running": true,
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ]
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "running": true,
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ]
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachineList](#schemav1.offlinevirtualmachinelist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachineList](#schemav1.offlinevirtualmachinelist)|

<aside class="success">
This operation does not require authentication
</aside>

## createNamespacedOfflineVirtualMachine

<a id="opIdcreateNamespacedOfflineVirtualMachine"></a>

> Code samples

`POST /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines`

*Create a OfflineVirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="createNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|body|body|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="createNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteCollectionNamespacedOfflineVirtualMachine

<a id="opIddeleteCollectionNamespacedOfflineVirtualMachine"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines`

*Delete a collection of OfflineVirtualMachine objects.*

<h3 id="deleteCollectionNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteCollectionNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## readNamespacedOfflineVirtualMachine

<a id="opIdreadNamespacedOfflineVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines/{name}`

*Get a OfflineVirtualMachine object.*

<h3 id="readNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|name|path|string|true|Name of the resource|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|exact|query|boolean|false|Should the export be exact. Exact export maintains cluster-specific fields like 'Namespace'.|
|export|query|boolean|false|Should this value be exported. Export strips fields that a user can not specify.|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="readNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## replaceNamespacedOfflineVirtualMachine

<a id="opIdreplaceNamespacedOfflineVirtualMachine"></a>

> Code samples

`PUT /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines/{name}`

*Update a OfflineVirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="replaceNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|body|body|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="replaceNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Create|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteNamespacedOfflineVirtualMachine

<a id="opIddeleteNamespacedOfflineVirtualMachine"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines/{name}`

*Delete a OfflineVirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "gracePeriodSeconds": 0,
  "kind": "string",
  "orphanDependents": true,
  "preconditions": {
    "uid": null
  },
  "propagationPolicy": null
}
```

<h3 id="deleteNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|gracePeriodSeconds|query|integer|false|The duration in seconds before the object should be deleted. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period for the specified type will be used. Defaults to a per object value if not specified. zero means delete immediately.|
|orphanDependents|query|boolean|false|Deprecated: please use the PropagationPolicy, this field will be deprecated in 1.7. Should the dependent objects be orphaned. If true/false, the "orphan" finalizer will be added to/removed from the object's finalizers list. Either this field or PropagationPolicy may be set, but not both.|
|propagationPolicy|query|string|false|Whether and how garbage collection will be performed. Either this field or OrphanDependents may be set, but not both. The default policy is decided by the existing finalizer set in the metadata.finalizers and the resource-specific default policy. Acceptable values are: 'Orphan' - orphan the dependents; 'Background' - allow the garbage collector to delete the dependents in the background; 'Foreground' - a cascading policy that deletes all dependents in the foreground.|
|body|body|[v1.DeleteOptions](#schemav1.deleteoptions)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## patchNamespacedOfflineVirtualMachine

<a id="opIdpatchNamespacedOfflineVirtualMachine"></a>

> Code samples

`PATCH /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/offlinevirtualmachines/{name}`

*Patch a OfflineVirtualMachine object.*

> Body parameter

```json
null
```

<h3 id="patchNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[v1.Patch](#schemav1.patch)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

<h3 id="patchNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## listNamespacedVirtualMachine

<a id="opIdlistNamespacedVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines`

*Get a list of VirtualMachine objects.*

<h3 id="listNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "interfaces": [
          {
            "ipAddress": "string",
            "mac": "string"
          }
        ],
        "nodeName": "string",
        "phase": "string"
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "interfaces": [
          {
            "ipAddress": "string",
            "mac": "string"
          }
        ],
        "nodeName": "string",
        "phase": "string"
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineList](#schemav1.virtualmachinelist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineList](#schemav1.virtualmachinelist)|

<aside class="success">
This operation does not require authentication
</aside>

## createNamespacedVirtualMachine

<a id="opIdcreateNamespacedVirtualMachine"></a>

> Code samples

`POST /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines`

*Create a VirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="createNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|body|body|[v1.VirtualMachine](#schemav1.virtualmachine)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="createNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[v1.VirtualMachine](#schemav1.virtualmachine)|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted|[v1.VirtualMachine](#schemav1.virtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteCollectionNamespacedVirtualMachine

<a id="opIddeleteCollectionNamespacedVirtualMachine"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines`

*Delete a collection of VirtualMachine objects.*

<h3 id="deleteCollectionNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteCollectionNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## readNamespacedVirtualMachine

<a id="opIdreadNamespacedVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}`

*Get a VirtualMachine object.*

<h3 id="readNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|name|path|string|true|Name of the resource|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|exact|query|boolean|false|Should the export be exact. Exact export maintains cluster-specific fields like 'Namespace'.|
|export|query|boolean|false|Should this value be exported. Export strips fields that a user can not specify.|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="readNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## replaceNamespacedVirtualMachine

<a id="opIdreplaceNamespacedVirtualMachine"></a>

> Code samples

`PUT /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}`

*Update a VirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="replaceNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|body|body|[v1.VirtualMachine](#schemav1.virtualmachine)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="replaceNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Create|[v1.VirtualMachine](#schemav1.virtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteNamespacedVirtualMachine

<a id="opIddeleteNamespacedVirtualMachine"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}`

*Delete a VirtualMachine object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "gracePeriodSeconds": 0,
  "kind": "string",
  "orphanDependents": true,
  "preconditions": {
    "uid": null
  },
  "propagationPolicy": null
}
```

<h3 id="deleteNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|gracePeriodSeconds|query|integer|false|The duration in seconds before the object should be deleted. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period for the specified type will be used. Defaults to a per object value if not specified. zero means delete immediately.|
|orphanDependents|query|boolean|false|Deprecated: please use the PropagationPolicy, this field will be deprecated in 1.7. Should the dependent objects be orphaned. If true/false, the "orphan" finalizer will be added to/removed from the object's finalizers list. Either this field or PropagationPolicy may be set, but not both.|
|propagationPolicy|query|string|false|Whether and how garbage collection will be performed. Either this field or OrphanDependents may be set, but not both. The default policy is decided by the existing finalizer set in the metadata.finalizers and the resource-specific default policy. Acceptable values are: 'Orphan' - orphan the dependents; 'Background' - allow the garbage collector to delete the dependents in the background; 'Foreground' - a cascading policy that deletes all dependents in the foreground.|
|body|body|[v1.DeleteOptions](#schemav1.deleteoptions)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## patchNamespacedVirtualMachine

<a id="opIdpatchNamespacedVirtualMachine"></a>

> Code samples

`PATCH /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}`

*Patch a VirtualMachine object.*

> Body parameter

```json
null
```

<h3 id="patchNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[v1.Patch](#schemav1.patch)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

<h3 id="patchNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachine](#schemav1.virtualmachine)|

<aside class="success">
This operation does not require authentication
</aside>

## listNamespacedVirtualMachineReplicaSet

<a id="opIdlistNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets`

*Get a list of VirtualMachineReplicaSet objects.*

<h3 id="listNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "paused": true,
        "replicas": 0,
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        },
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "readyReplicas": 0,
        "replicas": 0
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "paused": true,
        "replicas": 0,
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        },
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "readyReplicas": 0,
        "replicas": 0
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSetList](#schemav1.virtualmachinereplicasetlist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSetList](#schemav1.virtualmachinereplicasetlist)|

<aside class="success">
This operation does not require authentication
</aside>

## createNamespacedVirtualMachineReplicaSet

<a id="opIdcreateNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`POST /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets`

*Create a VirtualMachineReplicaSet object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="createNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|body|body|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="createNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteCollectionNamespacedVirtualMachineReplicaSet

<a id="opIddeleteCollectionNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets`

*Delete a collection of VirtualMachineReplicaSet objects.*

<h3 id="deleteCollectionNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteCollectionNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## readNamespacedVirtualMachineReplicaSet

<a id="opIdreadNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets/{name}`

*Get a VirtualMachineReplicaSet object.*

<h3 id="readNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|name|path|string|true|Name of the resource|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|exact|query|boolean|false|Should the export be exact. Exact export maintains cluster-specific fields like 'Namespace'.|
|export|query|boolean|false|Should this value be exported. Export strips fields that a user can not specify.|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="readNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|

<aside class="success">
This operation does not require authentication
</aside>

## replaceNamespacedVirtualMachineReplicaSet

<a id="opIdreplaceNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`PUT /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets/{name}`

*Update a VirtualMachineReplicaSet object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="replaceNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|body|body|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="replaceNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Create|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteNamespacedVirtualMachineReplicaSet

<a id="opIddeleteNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`DELETE /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets/{name}`

*Delete a VirtualMachineReplicaSet object.*

> Body parameter

```json
{
  "apiVersion": "string",
  "gracePeriodSeconds": 0,
  "kind": "string",
  "orphanDependents": true,
  "preconditions": {
    "uid": null
  },
  "propagationPolicy": null
}
```

<h3 id="deleteNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|
|gracePeriodSeconds|query|integer|false|The duration in seconds before the object should be deleted. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period for the specified type will be used. Defaults to a per object value if not specified. zero means delete immediately.|
|orphanDependents|query|boolean|false|Deprecated: please use the PropagationPolicy, this field will be deprecated in 1.7. Should the dependent objects be orphaned. If true/false, the "orphan" finalizer will be added to/removed from the object's finalizers list. Either this field or PropagationPolicy may be set, but not both.|
|propagationPolicy|query|string|false|Whether and how garbage collection will be performed. Either this field or OrphanDependents may be set, but not both. The default policy is decided by the existing finalizer set in the metadata.finalizers and the resource-specific default policy. Acceptable values are: 'Orphan' - orphan the dependents; 'Background' - allow the garbage collector to delete the dependents in the background; 'Foreground' - a cascading policy that deletes all dependents in the foreground.|
|body|body|[v1.DeleteOptions](#schemav1.deleteoptions)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

<h3 id="deleteNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.Status](#schemav1.status)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.Status](#schemav1.status)|

<aside class="success">
This operation does not require authentication
</aside>

## patchNamespacedVirtualMachineReplicaSet

<a id="opIdpatchNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`PATCH /apis/kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachinereplicasets/{name}`

*Patch a VirtualMachineReplicaSet object.*

> Body parameter

```json
null
```

<h3 id="patchNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[v1.Patch](#schemav1.patch)|true|No description|

> Example responses

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

<h3 id="patchNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)|

<aside class="success">
This operation does not require authentication
</aside>

## listOfflineVirtualMachineForAllNamespaces

<a id="opIdlistOfflineVirtualMachineForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/offlinevirtualmachines`

*Get a list of all OfflineVirtualMachine objects.*

<h3 id="listOfflineVirtualMachineForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "running": true,
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ]
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "running": true,
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ]
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listOfflineVirtualMachineForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.OfflineVirtualMachineList](#schemav1.offlinevirtualmachinelist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.OfflineVirtualMachineList](#schemav1.offlinevirtualmachinelist)|

<aside class="success">
This operation does not require authentication
</aside>

## listVirtualMachineForAllNamespaces

<a id="opIdlistVirtualMachineForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/virtualmachines`

*Get a list of all VirtualMachine objects.*

<h3 id="listVirtualMachineForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "interfaces": [
          {
            "ipAddress": "string",
            "mac": "string"
          }
        ],
        "nodeName": "string",
        "phase": "string"
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "interfaces": [
          {
            "ipAddress": "string",
            "mac": "string"
          }
        ],
        "nodeName": "string",
        "phase": "string"
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listVirtualMachineForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineList](#schemav1.virtualmachinelist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineList](#schemav1.virtualmachinelist)|

<aside class="success">
This operation does not require authentication
</aside>

## listVirtualMachineReplicaSetForAllNamespaces

<a id="opIdlistVirtualMachineReplicaSetForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/virtualmachinereplicasets`

*Get a list of all VirtualMachineReplicaSet objects.*

<h3 id="listVirtualMachineReplicaSetForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "paused": true,
        "replicas": 0,
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        },
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "readyReplicas": 0,
        "replicas": 0
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "paused": true,
        "replicas": 0,
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        },
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "readyReplicas": 0,
        "replicas": 0
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

<h3 id="listVirtualMachineReplicaSetForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.VirtualMachineReplicaSetList](#schemav1.virtualmachinereplicasetlist)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.VirtualMachineReplicaSetList](#schemav1.virtualmachinereplicasetlist)|

<aside class="success">
This operation does not require authentication
</aside>

## watchNamespacedOfflineVirtualMachine

<a id="opIdwatchNamespacedOfflineVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/namespaces/{namespace}/offlinevirtualmachines`

*Watch a OfflineVirtualMachine object.*

<h3 id="watchNamespacedOfflineVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchNamespacedOfflineVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## watchNamespacedVirtualMachine

<a id="opIdwatchNamespacedVirtualMachine"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/namespaces/{namespace}/virtualmachines`

*Watch a VirtualMachine object.*

<h3 id="watchNamespacedVirtualMachine-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchNamespacedVirtualMachine-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## watchNamespacedVirtualMachineReplicaSet

<a id="opIdwatchNamespacedVirtualMachineReplicaSet"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/namespaces/{namespace}/virtualmachinereplicasets`

*Watch a VirtualMachineReplicaSet object.*

<h3 id="watchNamespacedVirtualMachineReplicaSet-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchNamespacedVirtualMachineReplicaSet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## watchOfflineVirtualMachineListForAllNamespaces

<a id="opIdwatchOfflineVirtualMachineListForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/offlinevirtualmachines`

*Watch a OfflineVirtualMachineList object.*

<h3 id="watchOfflineVirtualMachineListForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchOfflineVirtualMachineListForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## watchVirtualMachineListForAllNamespaces

<a id="opIdwatchVirtualMachineListForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/virtualmachines`

*Watch a VirtualMachineList object.*

<h3 id="watchVirtualMachineListForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchVirtualMachineListForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## watchVirtualMachineReplicaSetListForAllNamespaces

<a id="opIdwatchVirtualMachineReplicaSetListForAllNamespaces"></a>

> Code samples

`GET /apis/kubevirt.io/v1alpha1/watch/virtualmachinereplicasets`

*Watch a VirtualMachineReplicaSetList object.*

<h3 id="watchVirtualMachineReplicaSetListForAllNamespaces-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|continue|query|string|false|The continue option should be set when retrieving more results from the server. Since this value is server defined, clients may only use the continue value from a previous query result with identical query parameters (except for the value of continue) and the server may reject a continue value it does not recognize. If the specified continue value is no longer valid whether due to expiration (generally five to fifteen minutes) or a configuration change on the server the server will respond with a 410 ResourceExpired error indicating the client must restart their list without the continue field. This field is not supported when watch is true. Clients may start a watch from the last resourceVersion value returned by the server and not miss any modifications.|
|fieldSelector|query|string|false|A selector to restrict the list of returned objects by their fields. Defaults to everything.|
|includeUninitialized|query|boolean|false|If true, partially initialized resources are included in the response.|
|labelSelector|query|string|false|A selector to restrict the list of returned objects by their labels. Defaults to everything|
|limit|query|integer|false|limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.|
|resourceVersion|query|string|false|When specified with a watch call, shows changes that occur after that particular version of a resource. Defaults to changes from the beginning of history.|
|timeoutSeconds|query|integer|false|TimeoutSeconds for the list/watch call.|
|watch|query|boolean|false|Watch for changes to the described resources and return them as a stream of add, update, and remove notifications. Specify resourceVersion.|

#### Detailed descriptions

**limit**: limit is a maximum number of responses to return for a list call. If more items exist, the server will set the `continue` field on the list metadata to a value that can be used with the same initial query to retrieve the next set of results. Setting a limit may return fewer than the requested amount of items (up to zero items) in the event all requested objects are filtered out and clients should only use the presence of the continue field to determine whether more results are available. Servers may choose not to support the limit argument and will return all of the available results. If limit is specified and the continue field is empty, clients may assume that no more results are available. This field is not supported if watch is true.

The server guarantees that the objects returned when using continue will be identical to issuing a single list call without a limit - that is, no objects created, modified, or deleted after the first request is issued will be included in any subsequent continued requests. This is sometimes referred to as a consistent snapshot, and ensures that a client that is using limit to receive smaller chunks of a very large result can ensure they see all possible objects. If objects are updated during a chunked list the version of the object that was present at the time the first list result was calculated is returned.

> Example responses

```json
{
  "object": "string",
  "type": "string"
}
```

```json
{
  "object": "string",
  "type": "string"
}
```

<h3 id="watchVirtualMachineReplicaSetListForAllNamespaces-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[v1.WatchEvent](#schemav1.watchevent)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|default|Default|OK|[v1.WatchEvent](#schemav1.watchevent)|

<aside class="success">
This operation does not require authentication
</aside>

## console

<a id="opIdconsole"></a>

> Code samples

`GET /apis/subresources.kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}/console`

*Open a websocket connection to a serial console on the specified VM.*

<h3 id="console-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|

<h3 id="console-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="success">
This operation does not require authentication
</aside>

## test

<a id="opIdtest"></a>

> Code samples

`GET /apis/subresources.kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}/test`

*Test endpoint verifying apiserver connectivity.*

<h3 id="test-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|

<h3 id="test-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="success">
This operation does not require authentication
</aside>

## vnc

<a id="opIdvnc"></a>

> Code samples

`GET /apis/subresources.kubevirt.io/v1alpha1/namespaces/{namespace}/virtualmachines/{name}/vnc`

*Open a websocket connection to connect to VNC on the specified VM.*

<h3 id="vnc-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|namespace|path|string|true|Object name and auth scope, such as for teams and projects|
|name|path|string|true|Name of the resource|

<h3 id="vnc-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocStypes.uid">types.UID</h2>

<a id="schematypes.uid"></a>

```json
null
```

### Properties

*None*

<h2 id="tocSv1.apigroup">v1.APIGroup</h2>

<a id="schemav1.apigroup"></a>

```json
{
  "apiVersion": "string",
  "kind": "string",
  "name": "string",
  "preferredVersion": {
    "groupVersion": "string",
    "version": "string"
  },
  "serverAddressByClientCIDRs": [
    {
      "clientCIDR": "string",
      "serverAddress": "string"
    }
  ],
  "versions": [
    {
      "groupVersion": "string",
      "version": "string"
    }
  ]
}
```

### Properties

*APIGroup contains the name, the supported versions, and the preferred version of a group.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|name|string|true|name is the name of the group.|
|preferredVersion|[v1.GroupVersionForDiscovery](#schemav1.groupversionfordiscovery)|false|No description|
|serverAddressByClientCIDRs|[[v1.ServerAddressByClientCIDR](#schemav1.serveraddressbyclientcidr)]|true|a map of client CIDR to server address that is serving this group. This is to help clients reach servers in the most network-efficient way possible. Clients can use the appropriate server address as per the CIDR that they match. In case of multiple matches, clients should use the longest matching CIDR. The server returns only those CIDRs that it thinks that the client can match. For example: the master will return an internal IP CIDR only, if the client reaches the server using an internal IP. Server looks at X-Forwarded-For header or X-Real-Ip header or request.RemoteAddr (in that order) to get the client IP.|
|versions|[[v1.GroupVersionForDiscovery](#schemav1.groupversionfordiscovery)]|true|versions are the versions supported in this group.|

<h2 id="tocSv1.apigrouplist">v1.APIGroupList</h2>

<a id="schemav1.apigrouplist"></a>

```json
{
  "apiVersion": "string",
  "groups": [
    {
      "apiVersion": "string",
      "kind": "string",
      "name": "string",
      "preferredVersion": {
        "groupVersion": "string",
        "version": "string"
      },
      "serverAddressByClientCIDRs": [
        {
          "clientCIDR": "string",
          "serverAddress": "string"
        }
      ],
      "versions": [
        {
          "groupVersion": "string",
          "version": "string"
        }
      ]
    }
  ],
  "kind": "string"
}
```

### Properties

*APIGroupList is a list of APIGroup, to allow clients to discover the API at /apis.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|groups|[[v1.APIGroup](#schemav1.apigroup)]|true|groups is a list of APIGroup.|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|

<h2 id="tocSv1.apiresource">v1.APIResource</h2>

<a id="schemav1.apiresource"></a>

```json
{
  "categories": [
    "string"
  ],
  "group": "string",
  "kind": "string",
  "name": "string",
  "namespaced": true,
  "shortNames": [
    "string"
  ],
  "singularName": "string",
  "verbs": [
    "string"
  ],
  "version": "string"
}
```

### Properties

*APIResource specifies the name of a resource and whether it is namespaced.*

|Name|Type|Required|Description|
|---|---|---|---|
|categories|[string]|false|categories is a list of the grouped resources this resource belongs to (e.g. 'all')|
|group|string|false|group is the preferred group of the resource.  Empty implies the group of the containing resource list. For subresources, this may have a different value, for example: Scale".|
|kind|string|true|kind is the kind for the resource (e.g. 'Foo' is the kind for a resource 'foo')|
|name|string|true|name is the plural name of the resource.|
|namespaced|boolean|true|namespaced indicates if a resource is namespaced or not.|
|shortNames|[string]|false|shortNames is a list of suggested short names of the resource.|
|singularName|string|true|singularName is the singular name of the resource.  This allows clients to handle plural and singular opaquely. The singularName is more correct for reporting status on a single item and both singular and plural are allowed from the kubectl CLI interface.|
|verbs|[string]|true|verbs is a list of supported kube verbs (this includes get, list, watch, create, update, patch, delete, deletecollection, and proxy)|
|version|string|false|version is the preferred version of the resource.  Empty implies the version of the containing resource list For subresources, this may have a different value, for example: v1 (while inside a v1beta1 version of the core resource's group)".|

<h2 id="tocSv1.apiresourcelist">v1.APIResourceList</h2>

<a id="schemav1.apiresourcelist"></a>

```json
{
  "apiVersion": "string",
  "groupVersion": "string",
  "kind": "string",
  "resources": [
    {
      "categories": [
        "string"
      ],
      "group": "string",
      "kind": "string",
      "name": "string",
      "namespaced": true,
      "shortNames": [
        "string"
      ],
      "singularName": "string",
      "verbs": [
        "string"
      ],
      "version": "string"
    }
  ]
}
```

### Properties

*APIResourceList is a list of APIResource, it is used to expose the name of the resources supported in a specific group and version, and if the resource is namespaced.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|groupVersion|string|true|groupVersion is the group and version this APIResourceList is for.|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|resources|[[v1.APIResource](#schemav1.apiresource)]|true|resources contains the name of the resources and if they are namespaced.|

<h2 id="tocSv1.affinity">v1.Affinity</h2>

<a id="schemav1.affinity"></a>

```json
{
  "nodeAffinity": {
    "preferredDuringSchedulingIgnoredDuringExecution": [
      {
        "preference": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ]
        },
        "weight": 0
      }
    ],
    "requiredDuringSchedulingIgnoredDuringExecution": {
      "nodeSelectorTerms": [
        {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Properties

*Affinity groups all the affinity rules related to a VM*

|Name|Type|Required|Description|
|---|---|---|---|
|nodeAffinity|[v1.NodeAffinity](#schemav1.nodeaffinity)|false|No description|

<h2 id="tocSv1.cdromtarget">v1.CDRomTarget</h2>

<a id="schemav1.cdromtarget"></a>

```json
{
  "bus": "string",
  "readonly": true,
  "tray": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|bus|string|false|Bus indicates the type of disk device to emulate. supported values: virtio, sata, scsi, ide|
|readonly|boolean|false|ReadOnly Defaults to true|
|tray|string|false|Tray indicates if the tray of the device is open or closed. Allowed values are "open" and "closed" Defaults to closed +optional|

<h2 id="tocSv1.cpu">v1.CPU</h2>

<a id="schemav1.cpu"></a>

```json
{
  "cores": 0
}
```

### Properties

*CPU allow specifying the CPU topology*

|Name|Type|Required|Description|
|---|---|---|---|
|cores|integer|false|Cores specifies the number of cores inside the vm. Must be a value greater or equal 1.|

<h2 id="tocSv1.clock">v1.Clock</h2>

<a id="schemav1.clock"></a>

```json
{
  "timer": {
    "hpet": {
      "present": true,
      "tickPolicy": "string"
    },
    "hyperv": {
      "present": true
    },
    "kvm": {
      "present": true
    },
    "pit": {
      "present": true,
      "tickPolicy": "string"
    },
    "rtc": {
      "present": true,
      "tickPolicy": "string",
      "track": "string"
    }
  },
  "timezone": null,
  "utc": {
    "offsetSeconds": 0
  }
}
```

### Properties

*Represents the clock and timers of a vm*

|Name|Type|Required|Description|
|---|---|---|---|
|timer|[v1.Timer](#schemav1.timer)|true|No description|
|timezone|[v1.ClockOffsetTimezone](#schemav1.clockoffsettimezone)|false|No description|
|utc|[v1.ClockOffsetUTC](#schemav1.clockoffsetutc)|false|No description|

<h2 id="tocSv1.clockoffsettimezone">v1.ClockOffsetTimezone</h2>

<a id="schemav1.clockoffsettimezone"></a>

```json
null
```

### Properties

*None*

<h2 id="tocSv1.clockoffsetutc">v1.ClockOffsetUTC</h2>

<a id="schemav1.clockoffsetutc"></a>

```json
{
  "offsetSeconds": 0
}
```

### Properties

*UTC sets the guest clock to UTC on each boot.*

|Name|Type|Required|Description|
|---|---|---|---|
|offsetSeconds|integer(int32)|false|OffsetSeconds specifies an offset in seconds, relative to UTC. If set, guest changes to the clock will be kept during reboots and not reset.|

<h2 id="tocSv1.cloudinitnocloudsource">v1.CloudInitNoCloudSource</h2>

<a id="schemav1.cloudinitnocloudsource"></a>

```json
{
  "secretRef": {
    "name": "string"
  },
  "userData": "string",
  "userDataBase64": "string"
}
```

### Properties

*Represents a cloud-init nocloud user data source
More info: http://cloudinit.readthedocs.io/en/latest/topics/datasources/nocloud.html*

|Name|Type|Required|Description|
|---|---|---|---|
|secretRef|[v1.LocalObjectReference](#schemav1.localobjectreference)|false|No description|
|userData|string|false|UserData contains NoCloud inline cloud-init userdata + optional|
|userDataBase64|string|false|UserDataBase64 contains NoCloud cloud-init userdata as a base64 encoded string + optional|

<h2 id="tocSv1.deleteoptions">v1.DeleteOptions</h2>

<a id="schemav1.deleteoptions"></a>

```json
{
  "apiVersion": "string",
  "gracePeriodSeconds": 0,
  "kind": "string",
  "orphanDependents": true,
  "preconditions": {
    "uid": null
  },
  "propagationPolicy": null
}
```

### Properties

*DeleteOptions may be provided when deleting an API object.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|gracePeriodSeconds|integer(int64)|false|The duration in seconds before the object should be deleted. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period for the specified type will be used. Defaults to a per object value if not specified. zero means delete immediately.|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|orphanDependents|boolean|false|Deprecated: please use the PropagationPolicy, this field will be deprecated in 1.7. Should the dependent objects be orphaned. If true/false, the "orphan" finalizer will be added to/removed from the object's finalizers list. Either this field or PropagationPolicy may be set, but not both.|
|preconditions|[v1.Preconditions](#schemav1.preconditions)|false|No description|
|propagationPolicy|[v1.DeletionPropagation](#schemav1.deletionpropagation)|false|No description|

<h2 id="tocSv1.deletionpropagation">v1.DeletionPropagation</h2>

<a id="schemav1.deletionpropagation"></a>

```json
null
```

### Properties

*None*

<h2 id="tocSv1.devices">v1.Devices</h2>

<a id="schemav1.devices"></a>

```json
{
  "disks": [
    {
      "cdrom": {
        "bus": "string",
        "readonly": true,
        "tray": "string"
      },
      "disk": {
        "bus": "string",
        "readonly": true
      },
      "floppy": {
        "readonly": true,
        "tray": "string"
      },
      "lun": {
        "bus": "string",
        "readonly": true
      },
      "name": "string",
      "volumeName": "string"
    }
  ],
  "watchdog": {
    "i6300esb": {
      "action": "string"
    },
    "name": "string"
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|disks|[[v1.Disk](#schemav1.disk)]|false|Disks describes disks, cdroms, floppy and luns which are connected to the vm|
|watchdog|[v1.Watchdog](#schemav1.watchdog)|false|No description|

<h2 id="tocSv1.disk">v1.Disk</h2>

<a id="schemav1.disk"></a>

```json
{
  "cdrom": {
    "bus": "string",
    "readonly": true,
    "tray": "string"
  },
  "disk": {
    "bus": "string",
    "readonly": true
  },
  "floppy": {
    "readonly": true,
    "tray": "string"
  },
  "lun": {
    "bus": "string",
    "readonly": true
  },
  "name": "string",
  "volumeName": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|cdrom|[v1.CDRomTarget](#schemav1.cdromtarget)|false|No description|
|disk|[v1.DiskTarget](#schemav1.disktarget)|false|No description|
|floppy|[v1.FloppyTarget](#schemav1.floppytarget)|false|No description|
|lun|[v1.LunTarget](#schemav1.luntarget)|false|No description|
|name|string|true|Name is the device name|
|volumeName|string|true|Name of the volume which is referenced Must match the Name of a Volume.|

<h2 id="tocSv1.disktarget">v1.DiskTarget</h2>

<a id="schemav1.disktarget"></a>

```json
{
  "bus": "string",
  "readonly": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|bus|string|false|Bus indicates the type of disk device to emulate. supported values: virtio, sata, scsi, ide|
|readonly|boolean|false|ReadOnly Defaults to false|

<h2 id="tocSv1.domainspec">v1.DomainSpec</h2>

<a id="schemav1.domainspec"></a>

```json
{
  "clock": {
    "timer": {
      "hpet": {
        "present": true,
        "tickPolicy": "string"
      },
      "hyperv": {
        "present": true
      },
      "kvm": {
        "present": true
      },
      "pit": {
        "present": true,
        "tickPolicy": "string"
      },
      "rtc": {
        "present": true,
        "tickPolicy": "string",
        "track": "string"
      }
    },
    "timezone": null,
    "utc": {
      "offsetSeconds": 0
    }
  },
  "cpu": {
    "cores": 0
  },
  "devices": {
    "disks": [
      {
        "cdrom": {
          "bus": "string",
          "readonly": true,
          "tray": "string"
        },
        "disk": {
          "bus": "string",
          "readonly": true
        },
        "floppy": {
          "readonly": true,
          "tray": "string"
        },
        "lun": {
          "bus": "string",
          "readonly": true
        },
        "name": "string",
        "volumeName": "string"
      }
    ],
    "watchdog": {
      "i6300esb": {
        "action": "string"
      },
      "name": "string"
    }
  },
  "features": {
    "acpi": {
      "enabled": true
    },
    "apic": {
      "enabled": true,
      "endOfInterrupt": true
    },
    "hyperv": {
      "relaxed": {
        "enabled": true
      },
      "reset": {
        "enabled": true
      },
      "runtime": {
        "enabled": true
      },
      "spinlocks": {
        "enabled": true,
        "spinlocks": 0
      },
      "synic": {
        "enabled": true
      },
      "synictimer": {
        "enabled": true
      },
      "vapic": {
        "enabled": true
      },
      "vendorid": {
        "enabled": true,
        "vendorid": "string"
      },
      "vpindex": {
        "enabled": true
      }
    }
  },
  "firmware": {
    "uuid": "string"
  },
  "machine": {
    "type": "string"
  },
  "resources": {
    "limits": {},
    "requests": {}
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|clock|[v1.Clock](#schemav1.clock)|false|No description|
|cpu|[v1.CPU](#schemav1.cpu)|false|No description|
|devices|[v1.Devices](#schemav1.devices)|true|No description|
|features|[v1.Features](#schemav1.features)|false|No description|
|firmware|[v1.Firmware](#schemav1.firmware)|false|No description|
|machine|[v1.Machine](#schemav1.machine)|false|No description|
|resources|[v1.ResourceRequirements](#schemav1.resourcerequirements)|false|No description|

<h2 id="tocSv1.emptydisksource">v1.EmptyDiskSource</h2>

<a id="schemav1.emptydisksource"></a>

```json
{
  "capacity": "string"
}
```

### Properties

*EmptyDisk represents a temporary disk which shares the vms lifecycle*

|Name|Type|Required|Description|
|---|---|---|---|
|capacity|string|true|Capacity of the sparse disk.|

<h2 id="tocSv1.ephemeralvolumesource">v1.EphemeralVolumeSource</h2>

<a id="schemav1.ephemeralvolumesource"></a>

```json
{
  "persistentVolumeClaim": {
    "claimName": "string",
    "readOnly": true
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|persistentVolumeClaim|[v1.PersistentVolumeClaimVolumeSource](#schemav1.persistentvolumeclaimvolumesource)|false|No description|

<h2 id="tocSv1.featureapic">v1.FeatureAPIC</h2>

<a id="schemav1.featureapic"></a>

```json
{
  "enabled": true,
  "endOfInterrupt": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|enabled|boolean|false|Enabled determines if the feature should be enabled or disabled on the guest Defaults to true +optional|
|endOfInterrupt|boolean|false|EndOfInterrupt enables the end of interrupt notification in the guest Defaults to false +optional|

<h2 id="tocSv1.featurehyperv">v1.FeatureHyperv</h2>

<a id="schemav1.featurehyperv"></a>

```json
{
  "relaxed": {
    "enabled": true
  },
  "reset": {
    "enabled": true
  },
  "runtime": {
    "enabled": true
  },
  "spinlocks": {
    "enabled": true,
    "spinlocks": 0
  },
  "synic": {
    "enabled": true
  },
  "synictimer": {
    "enabled": true
  },
  "vapic": {
    "enabled": true
  },
  "vendorid": {
    "enabled": true,
    "vendorid": "string"
  },
  "vpindex": {
    "enabled": true
  }
}
```

### Properties

*Hyperv specific features*

|Name|Type|Required|Description|
|---|---|---|---|
|relaxed|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|reset|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|runtime|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|spinlocks|[v1.FeatureSpinlocks](#schemav1.featurespinlocks)|false|No description|
|synic|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|synictimer|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|vapic|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|vendorid|[v1.FeatureVendorID](#schemav1.featurevendorid)|false|No description|
|vpindex|[v1.FeatureState](#schemav1.featurestate)|false|No description|

<h2 id="tocSv1.featurespinlocks">v1.FeatureSpinlocks</h2>

<a id="schemav1.featurespinlocks"></a>

```json
{
  "enabled": true,
  "spinlocks": 0
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|enabled|boolean|false|Enabled determines if the feature should be enabled or disabled on the guest Defaults to true +optional|
|spinlocks|integer|false|Retries indicates the number of retries Must be a value greater or equal 4096 Defaults to 4096 +optional|

<h2 id="tocSv1.featurestate">v1.FeatureState</h2>

<a id="schemav1.featurestate"></a>

```json
{
  "enabled": true
}
```

### Properties

*Represents if a feature is enabled or disabled*

|Name|Type|Required|Description|
|---|---|---|---|
|enabled|boolean|false|Enabled determines if the feature should be enabled or disabled on the guest Defaults to true +optional|

<h2 id="tocSv1.featurevendorid">v1.FeatureVendorID</h2>

<a id="schemav1.featurevendorid"></a>

```json
{
  "enabled": true,
  "vendorid": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|enabled|boolean|false|Enabled determines if the feature should be enabled or disabled on the guest Defaults to true +optional|
|vendorid|string|true|VendorID sets the hypervisor vendor id, visible to the vm String up to twelve characters|

<h2 id="tocSv1.features">v1.Features</h2>

<a id="schemav1.features"></a>

```json
{
  "acpi": {
    "enabled": true
  },
  "apic": {
    "enabled": true,
    "endOfInterrupt": true
  },
  "hyperv": {
    "relaxed": {
      "enabled": true
    },
    "reset": {
      "enabled": true
    },
    "runtime": {
      "enabled": true
    },
    "spinlocks": {
      "enabled": true,
      "spinlocks": 0
    },
    "synic": {
      "enabled": true
    },
    "synictimer": {
      "enabled": true
    },
    "vapic": {
      "enabled": true
    },
    "vendorid": {
      "enabled": true,
      "vendorid": "string"
    },
    "vpindex": {
      "enabled": true
    }
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|acpi|[v1.FeatureState](#schemav1.featurestate)|false|No description|
|apic|[v1.FeatureAPIC](#schemav1.featureapic)|false|No description|
|hyperv|[v1.FeatureHyperv](#schemav1.featurehyperv)|false|No description|

<h2 id="tocSv1.firmware">v1.Firmware</h2>

<a id="schemav1.firmware"></a>

```json
{
  "uuid": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|uuid|string|false|UUID reported by the vm bios Defaults to a random generated uid|

<h2 id="tocSv1.floppytarget">v1.FloppyTarget</h2>

<a id="schemav1.floppytarget"></a>

```json
{
  "readonly": true,
  "tray": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|readonly|boolean|false|ReadOnly Defaults to false|
|tray|string|false|Tray indicates if the tray of the device is open or closed. Allowed values are "open" and "closed" Defaults to closed +optional|

<h2 id="tocSv1.groupversionfordiscovery">v1.GroupVersionForDiscovery</h2>

<a id="schemav1.groupversionfordiscovery"></a>

```json
{
  "groupVersion": "string",
  "version": "string"
}
```

### Properties

*GroupVersion contains the "group/version" and "version" string of a version. It is made a struct to keep extensibility.*

|Name|Type|Required|Description|
|---|---|---|---|
|groupVersion|string|true|groupVersion specifies the API group and version in the form "group/version"|
|version|string|true|version specifies the version in the form of "version". This is to save the clients the trouble of splitting the GroupVersion.|

<h2 id="tocSv1.hpettimer">v1.HPETTimer</h2>

<a id="schemav1.hpettimer"></a>

```json
{
  "present": true,
  "tickPolicy": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|present|boolean|false|Enabled set to false makes sure that the machine type or a preset can't add the timer. Defaults to true +optional|
|tickPolicy|string|false|TickPolicy determines what happens when QEMU misses a deadline for injecting a tick to the guest One of "delay", "catchup", "merge", "discard"|

<h2 id="tocSv1.hypervtimer">v1.HypervTimer</h2>

<a id="schemav1.hypervtimer"></a>

```json
{
  "present": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|present|boolean|false|Enabled set to false makes sure that the machine type or a preset can't add the timer. Defaults to true +optional|

<h2 id="tocSv1.i6300esbwatchdog">v1.I6300ESBWatchdog</h2>

<a id="schemav1.i6300esbwatchdog"></a>

```json
{
  "action": "string"
}
```

### Properties

*i6300esb watchdog device*

|Name|Type|Required|Description|
|---|---|---|---|
|action|string|false|The action to take. Valid values are poweroff, reset, shutdown. Defaults to reset|

<h2 id="tocSv1.initializer">v1.Initializer</h2>

<a id="schemav1.initializer"></a>

```json
{
  "name": "string"
}
```

### Properties

*Initializer is information about an initializer that has not yet completed.*

|Name|Type|Required|Description|
|---|---|---|---|
|name|string|true|name of the process that is responsible for initializing this object.|

<h2 id="tocSv1.initializers">v1.Initializers</h2>

<a id="schemav1.initializers"></a>

```json
{
  "pending": [
    {
      "name": "string"
    }
  ],
  "result": {
    "apiVersion": "string",
    "code": 0,
    "details": {
      "causes": [
        {
          "field": "string",
          "message": "string",
          "reason": "string"
        }
      ],
      "group": "string",
      "kind": "string",
      "name": "string",
      "retryAfterSeconds": 0,
      "uid": "string"
    },
    "kind": "string",
    "message": "string",
    "metadata": {
      "continue": "string",
      "resourceVersion": "string",
      "selfLink": "string"
    },
    "reason": "string",
    "status": "string"
  }
}
```

### Properties

*Initializers tracks the progress of initialization.*

|Name|Type|Required|Description|
|---|---|---|---|
|pending|[[v1.Initializer](#schemav1.initializer)]|true|Pending is a list of initializers that must execute in order before this object is visible. When the last pending initializer is removed, and no failing result is set, the initializers struct will be set to nil and the object is considered as initialized and visible to all clients.|
|result|[v1.Status](#schemav1.status)|false|No description|

<h2 id="tocSv1.kvmtimer">v1.KVMTimer</h2>

<a id="schemav1.kvmtimer"></a>

```json
{
  "present": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|present|boolean|false|Enabled set to false makes sure that the machine type or a preset can't add the timer. Defaults to true +optional|

<h2 id="tocSv1.labelselector">v1.LabelSelector</h2>

<a id="schemav1.labelselector"></a>

```json
{
  "matchExpressions": [
    {
      "key": "string",
      "operator": "string",
      "values": [
        "string"
      ]
    }
  ],
  "matchLabels": {}
}
```

### Properties

*A label selector is a label query over a set of resources. The result of matchLabels and matchExpressions are ANDed. An empty label selector matches all objects. A null label selector matches no objects.*

|Name|Type|Required|Description|
|---|---|---|---|
|matchExpressions|[[v1.LabelSelectorRequirement](#schemav1.labelselectorrequirement)]|false|matchExpressions is a list of label selector requirements. The requirements are ANDed.|
|matchLabels|object|false|matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed.|

<h2 id="tocSv1.labelselectorrequirement">v1.LabelSelectorRequirement</h2>

<a id="schemav1.labelselectorrequirement"></a>

```json
{
  "key": "string",
  "operator": "string",
  "values": [
    "string"
  ]
}
```

### Properties

*A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.*

|Name|Type|Required|Description|
|---|---|---|---|
|key|string|true|key is the label key that the selector applies to.|
|operator|string|true|operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist.|
|values|[string]|false|values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch.|

<h2 id="tocSv1.listmeta">v1.ListMeta</h2>

<a id="schemav1.listmeta"></a>

```json
{
  "continue": "string",
  "resourceVersion": "string",
  "selfLink": "string"
}
```

### Properties

*ListMeta describes metadata that synthetic resources must have, including lists and various status objects. A resource may have only one of {ObjectMeta, ListMeta}.*

|Name|Type|Required|Description|
|---|---|---|---|
|continue|string|false|continue may be set if the user set a limit on the number of items returned, and indicates that the server has more data available. The value is opaque and may be used to issue another request to the endpoint that served this list to retrieve the next set of available objects. Continuing a list may not be possible if the server configuration has changed or more than a few minutes have passed. The resourceVersion field returned when using this continue value will be identical to the value in the first response.|
|resourceVersion|string|false|String that identifies the server's internal version of this object that can be used by clients to determine when objects have changed. Value must be treated as opaque by clients and passed unmodified back to the server. Populated by the system. Read-only. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#concurrency-control-and-consistency|
|selfLink|string|false|selfLink is a URL representing this object. Populated by the system. Read-only.|

<h2 id="tocSv1.localobjectreference">v1.LocalObjectReference</h2>

<a id="schemav1.localobjectreference"></a>

```json
{
  "name": "string"
}
```

### Properties

*LocalObjectReference contains enough information to let you locate the referenced object inside the same namespace.*

|Name|Type|Required|Description|
|---|---|---|---|
|name|string|false|Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names|

<h2 id="tocSv1.luntarget">v1.LunTarget</h2>

<a id="schemav1.luntarget"></a>

```json
{
  "bus": "string",
  "readonly": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|bus|string|false|Bus indicates the type of disk device to emulate. supported values: virtio, sata, scsi, ide|
|readonly|boolean|false|ReadOnly Defaults to false|

<h2 id="tocSv1.machine">v1.Machine</h2>

<a id="schemav1.machine"></a>

```json
{
  "type": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|type|string|true|QEMU machine type is the actual chipset of the VM.|

<h2 id="tocSv1.nodeaffinity">v1.NodeAffinity</h2>

<a id="schemav1.nodeaffinity"></a>

```json
{
  "preferredDuringSchedulingIgnoredDuringExecution": [
    {
      "preference": {
        "matchExpressions": [
          {
            "key": "string",
            "operator": "string",
            "values": [
              "string"
            ]
          }
        ]
      },
      "weight": 0
    }
  ],
  "requiredDuringSchedulingIgnoredDuringExecution": {
    "nodeSelectorTerms": [
      {
        "matchExpressions": [
          {
            "key": "string",
            "operator": "string",
            "values": [
              "string"
            ]
          }
        ]
      }
    ]
  }
}
```

### Properties

*Node affinity is a group of node affinity scheduling rules.*

|Name|Type|Required|Description|
|---|---|---|---|
|preferredDuringSchedulingIgnoredDuringExecution|[[v1.PreferredSchedulingTerm](#schemav1.preferredschedulingterm)]|false|The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred.|
|requiredDuringSchedulingIgnoredDuringExecution|[v1.NodeSelector](#schemav1.nodeselector)|false|No description|

<h2 id="tocSv1.nodeselector">v1.NodeSelector</h2>

<a id="schemav1.nodeselector"></a>

```json
{
  "nodeSelectorTerms": [
    {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ]
    }
  ]
}
```

### Properties

*A node selector represents the union of the results of one or more label queries over a set of nodes; that is, it represents the OR of the selectors represented by the node selector terms.*

|Name|Type|Required|Description|
|---|---|---|---|
|nodeSelectorTerms|[[v1.NodeSelectorTerm](#schemav1.nodeselectorterm)]|true|Required. A list of node selector terms. The terms are ORed.|

<h2 id="tocSv1.nodeselectorrequirement">v1.NodeSelectorRequirement</h2>

<a id="schemav1.nodeselectorrequirement"></a>

```json
{
  "key": "string",
  "operator": "string",
  "values": [
    "string"
  ]
}
```

### Properties

*A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.*

|Name|Type|Required|Description|
|---|---|---|---|
|key|string|true|The label key that the selector applies to.|
|operator|string|true|Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt.|
|values|[string]|false|An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch.|

<h2 id="tocSv1.nodeselectorterm">v1.NodeSelectorTerm</h2>

<a id="schemav1.nodeselectorterm"></a>

```json
{
  "matchExpressions": [
    {
      "key": "string",
      "operator": "string",
      "values": [
        "string"
      ]
    }
  ]
}
```

### Properties

*A null or empty node selector term matches no objects.*

|Name|Type|Required|Description|
|---|---|---|---|
|matchExpressions|[[v1.NodeSelectorRequirement](#schemav1.nodeselectorrequirement)]|true|Required. A list of node selector requirements. The requirements are ANDed.|

<h2 id="tocSv1.objectmeta">v1.ObjectMeta</h2>

<a id="schemav1.objectmeta"></a>

```json
{
  "annotations": {},
  "clusterName": "string",
  "creationTimestamp": "string",
  "deletionGracePeriodSeconds": 0,
  "deletionTimestamp": "string",
  "finalizers": [
    "string"
  ],
  "generateName": "string",
  "generation": 0,
  "initializers": {
    "pending": [
      {
        "name": "string"
      }
    ],
    "result": {
      "apiVersion": "string",
      "code": 0,
      "details": {
        "causes": [
          {
            "field": "string",
            "message": "string",
            "reason": "string"
          }
        ],
        "group": "string",
        "kind": "string",
        "name": "string",
        "retryAfterSeconds": 0,
        "uid": "string"
      },
      "kind": "string",
      "message": "string",
      "metadata": {
        "continue": "string",
        "resourceVersion": "string",
        "selfLink": "string"
      },
      "reason": "string",
      "status": "string"
    }
  },
  "labels": {},
  "name": "string",
  "namespace": "string",
  "ownerReferences": [
    {
      "apiVersion": "string",
      "blockOwnerDeletion": true,
      "controller": true,
      "kind": "string",
      "name": "string",
      "uid": "string"
    }
  ],
  "resourceVersion": "string",
  "selfLink": "string",
  "uid": "string"
}
```

### Properties

*ObjectMeta is metadata that all persisted resources must have, which includes all objects users must create.*

|Name|Type|Required|Description|
|---|---|---|---|
|annotations|object|false|Annotations is an unstructured key value map stored with a resource that may be set by external tools to store and retrieve arbitrary metadata. They are not queryable and should be preserved when modifying objects. More info: http://kubernetes.io/docs/user-guide/annotations|
|clusterName|string|false|The name of the cluster which the object belongs to. This is used to distinguish resources with same name and namespace in different clusters. This field is not set anywhere right now and apiserver is going to ignore it if set in create or update request.|
|creationTimestamp|string|false|CreationTimestamp is a timestamp representing the server time when this object was created. It is not guaranteed to be set in happens-before order across separate operations. Clients may not set this value. It is represented in RFC3339 form and is in UTC.  Populated by the system. Read-only. Null for lists. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#metadata|
|deletionGracePeriodSeconds|integer(int64)|false|Number of seconds allowed for this object to gracefully terminate before it will be removed from the system. Only set when deletionTimestamp is also set. May only be shortened. Read-only.|
|deletionTimestamp|string|false|DeletionTimestamp is RFC 3339 date and time at which this resource will be deleted. This field is set by the server when a graceful deletion is requested by the user, and is not directly settable by a client. The resource is expected to be deleted (no longer visible from resource lists, and not reachable by name) after the time in this field, once the finalizers list is empty. As long as the finalizers list contains items, deletion is blocked. Once the deletionTimestamp is set, this value may not be unset or be set further into the future, although it may be shortened or the resource may be deleted prior to this time. For example, a user may request that a pod is deleted in 30 seconds. The Kubelet will react by sending a graceful termination signal to the containers in the pod. After that 30 seconds, the Kubelet will send a hard termination signal (SIGKILL) to the container and after cleanup, remove the pod from the API. In the presence of network partitions, this object may still exist after this timestamp, until an administrator or automated process can determine the resource is fully terminated. If not set, graceful deletion of the object has not been requested.  Populated by the system when a graceful deletion is requested. Read-only. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#metadata|
|finalizers|[string]|false|Must be empty before the object is deleted from the registry. Each entry is an identifier for the responsible component that will remove the entry from the list. If the deletionTimestamp of the object is non-nil, entries in this list can only be removed.|
|generateName|string|false|GenerateName is an optional prefix, used by the server, to generate a unique name ONLY IF the Name field has not been provided. If this field is used, the name returned to the client will be different than the name passed. This value will also be combined with a unique suffix. The provided value has the same validation rules as the Name field, and may be truncated by the length of the suffix required to make the value unique on the server.  If this field is specified and the generated name exists, the server will NOT return a 409 - instead, it will either return 201 Created or 500 with Reason ServerTimeout indicating a unique name could not be found in the time allotted, and the client should retry (optionally after the time indicated in the Retry-After header).  Applied only if Name is not specified. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#idempotency|
|generation|integer(int64)|false|A sequence number representing a specific generation of the desired state. Populated by the system. Read-only.|
|initializers|[v1.Initializers](#schemav1.initializers)|false|No description|
|labels|object|false|Map of string keys and values that can be used to organize and categorize (scope and select) objects. May match selectors of replication controllers and services. More info: http://kubernetes.io/docs/user-guide/labels|
|name|string|false|Name must be unique within a namespace. Is required when creating resources, although some resources may allow a client to request the generation of an appropriate name automatically. Name is primarily intended for creation idempotence and configuration definition. Cannot be updated. More info: http://kubernetes.io/docs/user-guide/identifiers#names|
|namespace|string|false|Namespace defines the space within each name must be unique. An empty namespace is equivalent to the "default" namespace, but "default" is the canonical representation. Not all objects are required to be scoped to a namespace - the value of this field for those objects will be empty.  Must be a DNS_LABEL. Cannot be updated. More info: http://kubernetes.io/docs/user-guide/namespaces|
|ownerReferences|[[v1.OwnerReference](#schemav1.ownerreference)]|false|List of objects depended by this object. If ALL objects in the list have been deleted, this object will be garbage collected. If this object is managed by a controller, then an entry in this list will point to this controller, with the controller field set to true. There cannot be more than one managing controller.|
|resourceVersion|string|false|An opaque value that represents the internal version of this object that can be used by clients to determine when objects have changed. May be used for optimistic concurrency, change detection, and the watch operation on a resource or set of resources. Clients must treat these values as opaque and passed unmodified back to the server. They may only be valid for a particular resource or set of resources.  Populated by the system. Read-only. Value must be treated as opaque by clients and . More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#concurrency-control-and-consistency|
|selfLink|string|false|SelfLink is a URL representing this object. Populated by the system. Read-only.|
|uid|string|false|UID is the unique in time and space value for this object. It is typically generated by the server on successful creation of a resource and is not allowed to change on PUT operations.  Populated by the system. Read-only. More info: http://kubernetes.io/docs/user-guide/identifiers#uids|

<h2 id="tocSv1.offlinevirtualmachine">v1.OfflineVirtualMachine</h2>

<a id="schemav1.offlinevirtualmachine"></a>

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "running": true,
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ]
  }
}
```

### Properties

*OfflineVirtualMachine handles the VirtualMachines that are not running
or are in a stopped state
The OfflineVirtualMachine contains the template to create the
VirtualMachine. It also mirrors the running state of the created
VirtualMachine in its status.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ObjectMeta](#schemav1.objectmeta)|false|No description|
|spec|[v1.OfflineVirtualMachineSpec](#schemav1.offlinevirtualmachinespec)|false|No description|
|status|[v1.OfflineVirtualMachineStatus](#schemav1.offlinevirtualmachinestatus)|false|No description|

<h2 id="tocSv1.offlinevirtualmachinecondition">v1.OfflineVirtualMachineCondition</h2>

<a id="schemav1.offlinevirtualmachinecondition"></a>

```json
{
  "lastProbeTime": "string",
  "lastTransitionTime": "string",
  "message": "string",
  "reason": "string",
  "status": "string",
  "type": "string"
}
```

### Properties

*OfflineVirtualMachineCondition represents the state of OfflineVirtualMachine*

|Name|Type|Required|Description|
|---|---|---|---|
|lastProbeTime|string|false|No description|
|lastTransitionTime|string|false|No description|
|message|string|false|No description|
|reason|string|false|No description|
|status|string|true|No description|
|type|string|true|No description|

<h2 id="tocSv1.offlinevirtualmachinelist">v1.OfflineVirtualMachineList</h2>

<a id="schemav1.offlinevirtualmachinelist"></a>

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "running": true,
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ]
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

### Properties

*OfflineVirtualMachineList is a list of offlinevirtualmachines*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|items|[[v1.OfflineVirtualMachine](#schemav1.offlinevirtualmachine)]|true|Items is a list of OfflineVirtualMachines|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ListMeta](#schemav1.listmeta)|true|No description|

<h2 id="tocSv1.offlinevirtualmachinespec">v1.OfflineVirtualMachineSpec</h2>

<a id="schemav1.offlinevirtualmachinespec"></a>

```json
{
  "running": true,
  "template": {
    "metadata": {
      "annotations": {},
      "clusterName": "string",
      "creationTimestamp": "string",
      "deletionGracePeriodSeconds": 0,
      "deletionTimestamp": "string",
      "finalizers": [
        "string"
      ],
      "generateName": "string",
      "generation": 0,
      "initializers": {
        "pending": [
          {
            "name": "string"
          }
        ],
        "result": {
          "apiVersion": "string",
          "code": 0,
          "details": {
            "causes": [
              {
                "field": "string",
                "message": "string",
                "reason": "string"
              }
            ],
            "group": "string",
            "kind": "string",
            "name": "string",
            "retryAfterSeconds": 0,
            "uid": "string"
          },
          "kind": "string",
          "message": "string",
          "metadata": {
            "continue": "string",
            "resourceVersion": "string",
            "selfLink": "string"
          },
          "reason": "string",
          "status": "string"
        }
      },
      "labels": {},
      "name": "string",
      "namespace": "string",
      "ownerReferences": [
        {
          "apiVersion": "string",
          "blockOwnerDeletion": true,
          "controller": true,
          "kind": "string",
          "name": "string",
          "uid": "string"
        }
      ],
      "resourceVersion": "string",
      "selfLink": "string",
      "uid": "string"
    },
    "spec": {
      "affinity": {
        "nodeAffinity": {
          "preferredDuringSchedulingIgnoredDuringExecution": [
            {
              "preference": {
                "matchExpressions": [
                  {
                    "key": "string",
                    "operator": "string",
                    "values": []
                  }
                ]
              },
              "weight": 0
            }
          ],
          "requiredDuringSchedulingIgnoredDuringExecution": {
            "nodeSelectorTerms": [
              {
                "matchExpressions": [
                  {
                    "key": "string",
                    "operator": "string",
                    "values": []
                  }
                ]
              }
            ]
          }
        }
      },
      "domain": {
        "clock": {
          "timer": {
            "hpet": {
              "present": true,
              "tickPolicy": "string"
            },
            "hyperv": {
              "present": true
            },
            "kvm": {
              "present": true
            },
            "pit": {
              "present": true,
              "tickPolicy": "string"
            },
            "rtc": {
              "present": true,
              "tickPolicy": "string",
              "track": "string"
            }
          },
          "timezone": null,
          "utc": {
            "offsetSeconds": 0
          }
        },
        "cpu": {
          "cores": 0
        },
        "devices": {
          "disks": [
            {
              "cdrom": {
                "bus": "string",
                "readonly": true,
                "tray": "string"
              },
              "disk": {
                "bus": "string",
                "readonly": true
              },
              "floppy": {
                "readonly": true,
                "tray": "string"
              },
              "lun": {
                "bus": "string",
                "readonly": true
              },
              "name": "string",
              "volumeName": "string"
            }
          ],
          "watchdog": {
            "i6300esb": {
              "action": "string"
            },
            "name": "string"
          }
        },
        "features": {
          "acpi": {
            "enabled": true
          },
          "apic": {
            "enabled": true,
            "endOfInterrupt": true
          },
          "hyperv": {
            "relaxed": {
              "enabled": true
            },
            "reset": {
              "enabled": true
            },
            "runtime": {
              "enabled": true
            },
            "spinlocks": {
              "enabled": true,
              "spinlocks": 0
            },
            "synic": {
              "enabled": true
            },
            "synictimer": {
              "enabled": true
            },
            "vapic": {
              "enabled": true
            },
            "vendorid": {
              "enabled": true,
              "vendorid": "string"
            },
            "vpindex": {
              "enabled": true
            }
          }
        },
        "firmware": {
          "uuid": "string"
        },
        "machine": {
          "type": "string"
        },
        "resources": {
          "limits": {},
          "requests": {}
        }
      },
      "nodeSelector": {},
      "terminationGracePeriodSeconds": 0,
      "volumes": [
        {
          "cloudInitNoCloud": {
            "secretRef": {
              "name": "string"
            },
            "userData": "string",
            "userDataBase64": "string"
          },
          "emptyDisk": {
            "capacity": "string"
          },
          "ephemeral": {
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            }
          },
          "name": "string",
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          },
          "registryDisk": {
            "image": "string",
            "imagePullSecret": "string"
          }
        }
      ]
    }
  }
}
```

### Properties

*OfflineVirtualMachineSpec describes how the proper OfflineVirtualMachine
should look like*

|Name|Type|Required|Description|
|---|---|---|---|
|running|boolean|true|Running controlls whether the associatied VirtualMachine is created or not|
|template|[v1.VMTemplateSpec](#schemav1.vmtemplatespec)|true|No description|

<h2 id="tocSv1.offlinevirtualmachinestatus">v1.OfflineVirtualMachineStatus</h2>

<a id="schemav1.offlinevirtualmachinestatus"></a>

```json
{
  "conditions": [
    {
      "lastProbeTime": "string",
      "lastTransitionTime": "string",
      "message": "string",
      "reason": "string",
      "status": "string",
      "type": "string"
    }
  ]
}
```

### Properties

*OfflineVirtualMachineStatus represents the status returned by the
controller to describe how the OfflineVirtualMachine is doing*

|Name|Type|Required|Description|
|---|---|---|---|
|conditions|[[v1.OfflineVirtualMachineCondition](#schemav1.offlinevirtualmachinecondition)]|false|Hold the state information of the OfflineVirtualMachine and its VirtualMachine|

<h2 id="tocSv1.ownerreference">v1.OwnerReference</h2>

<a id="schemav1.ownerreference"></a>

```json
{
  "apiVersion": "string",
  "blockOwnerDeletion": true,
  "controller": true,
  "kind": "string",
  "name": "string",
  "uid": "string"
}
```

### Properties

*OwnerReference contains enough information to let you identify an owning object. Currently, an owning object must be in the same namespace, so there is no namespace field.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|true|API version of the referent.|
|blockOwnerDeletion|boolean|false|If true, AND if the owner has the "foregroundDeletion" finalizer, then the owner cannot be deleted from the key-value store until this reference is removed. Defaults to false. To set this field, a user needs "delete" permission of the owner, otherwise 422 (Unprocessable Entity) will be returned.|
|controller|boolean|false|If true, this reference points to the managing controller.|
|kind|string|true|Kind of the referent. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|name|string|true|Name of the referent. More info: http://kubernetes.io/docs/user-guide/identifiers#names|
|uid|string|true|UID of the referent. More info: http://kubernetes.io/docs/user-guide/identifiers#uids|

<h2 id="tocSv1.pittimer">v1.PITTimer</h2>

<a id="schemav1.pittimer"></a>

```json
{
  "present": true,
  "tickPolicy": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|present|boolean|false|Enabled set to false makes sure that the machine type or a preset can't add the timer. Defaults to true +optional|
|tickPolicy|string|false|TickPolicy determines what happens when QEMU misses a deadline for injecting a tick to the guest One of "delay", "catchup", "discard"|

<h2 id="tocSv1.patch">v1.Patch</h2>

<a id="schemav1.patch"></a>

```json
null
```

### Properties

*Patch is provided to give a concrete name and type to the Kubernetes PATCH request body.*

*None*

<h2 id="tocSv1.persistentvolumeclaimvolumesource">v1.PersistentVolumeClaimVolumeSource</h2>

<a id="schemav1.persistentvolumeclaimvolumesource"></a>

```json
{
  "claimName": "string",
  "readOnly": true
}
```

### Properties

*PersistentVolumeClaimVolumeSource references the user's PVC in the same namespace. This volume finds the bound PV and mounts that volume for the pod. A PersistentVolumeClaimVolumeSource is, essentially, a wrapper around another type of volume that is owned by someone else (the system).*

|Name|Type|Required|Description|
|---|---|---|---|
|claimName|string|true|ClaimName is the name of a PersistentVolumeClaim in the same namespace as the pod using this volume. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#persistentvolumeclaims|
|readOnly|boolean|false|Will force the ReadOnly setting in VolumeMounts. Default false.|

<h2 id="tocSv1.preconditions">v1.Preconditions</h2>

<a id="schemav1.preconditions"></a>

```json
{
  "uid": null
}
```

### Properties

*Preconditions must be fulfilled before an operation (update, delete, etc.) is carried out.*

|Name|Type|Required|Description|
|---|---|---|---|
|uid|[types.UID](#schematypes.uid)|false|No description|

<h2 id="tocSv1.preferredschedulingterm">v1.PreferredSchedulingTerm</h2>

<a id="schemav1.preferredschedulingterm"></a>

```json
{
  "preference": {
    "matchExpressions": [
      {
        "key": "string",
        "operator": "string",
        "values": [
          "string"
        ]
      }
    ]
  },
  "weight": 0
}
```

### Properties

*An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).*

|Name|Type|Required|Description|
|---|---|---|---|
|preference|[v1.NodeSelectorTerm](#schemav1.nodeselectorterm)|true|No description|
|weight|integer(int32)|true|Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100.|

<h2 id="tocSv1.rtctimer">v1.RTCTimer</h2>

<a id="schemav1.rtctimer"></a>

```json
{
  "present": true,
  "tickPolicy": "string",
  "track": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|present|boolean|false|Enabled set to false makes sure that the machine type or a preset can't add the timer. Defaults to true +optional|
|tickPolicy|string|false|TickPolicy determines what happens when QEMU misses a deadline for injecting a tick to the guest One of "delay", "catchup"|
|track|string|false|Track the guest or the wall clock|

<h2 id="tocSv1.registrydisksource">v1.RegistryDiskSource</h2>

<a id="schemav1.registrydisksource"></a>

```json
{
  "image": "string",
  "imagePullSecret": "string"
}
```

### Properties

*Represents a docker image with an embedded disk*

|Name|Type|Required|Description|
|---|---|---|---|
|image|string|true|Image is the name of the image with the embedded disk|
|imagePullSecret|string|false|ImagePullSecret is the name of the Docker registry secret required to pull the image. The secret must already exist.|

<h2 id="tocSv1.resourcerequirements">v1.ResourceRequirements</h2>

<a id="schemav1.resourcerequirements"></a>

```json
{
  "limits": {},
  "requests": {}
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|limits|object|false|Limits describes the maximum amount of compute resources allowed. Valid resource keys are "memory" and "cpu". +optional|
|requests|object|false|Requests is a description of the initial vm resources. Valid resource keys are "memory" and "cpu". +optional|

<h2 id="tocSv1.serveraddressbyclientcidr">v1.ServerAddressByClientCIDR</h2>

<a id="schemav1.serveraddressbyclientcidr"></a>

```json
{
  "clientCIDR": "string",
  "serverAddress": "string"
}
```

### Properties

*ServerAddressByClientCIDR helps the client to determine the server address that they should use, depending on the clientCIDR that they match.*

|Name|Type|Required|Description|
|---|---|---|---|
|clientCIDR|string|true|The CIDR with which clients can match their IP to figure out the server address that they should use.|
|serverAddress|string|true|Address of this server, suitable for a client that matches the above CIDR. This can be a hostname, hostname:port, IP or IP:port.|

<h2 id="tocSv1.status">v1.Status</h2>

<a id="schemav1.status"></a>

```json
{
  "apiVersion": "string",
  "code": 0,
  "details": {
    "causes": [
      {
        "field": "string",
        "message": "string",
        "reason": "string"
      }
    ],
    "group": "string",
    "kind": "string",
    "name": "string",
    "retryAfterSeconds": 0,
    "uid": "string"
  },
  "kind": "string",
  "message": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  },
  "reason": "string",
  "status": "string"
}
```

### Properties

*Status is a return value for calls that don't return other objects.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|code|integer(int32)|false|Suggested HTTP return code for this status, 0 if not set.|
|details|[v1.StatusDetails](#schemav1.statusdetails)|false|No description|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|message|string|false|A human-readable description of the status of this operation.|
|metadata|[v1.ListMeta](#schemav1.listmeta)|false|No description|
|reason|string|false|A machine-readable description of why this operation is in the "Failure" status. If this value is empty there is no information available. A Reason clarifies an HTTP status code but does not override it.|
|status|string|false|Status of the operation. One of: "Success" or "Failure". More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#spec-and-status|

<h2 id="tocSv1.statuscause">v1.StatusCause</h2>

<a id="schemav1.statuscause"></a>

```json
{
  "field": "string",
  "message": "string",
  "reason": "string"
}
```

### Properties

*StatusCause provides more information about an api.Status failure, including cases when multiple errors are encountered.*

|Name|Type|Required|Description|
|---|---|---|---|
|field|string|false|The field of the resource that has caused this error, as named by its JSON serialization. May include dot and postfix notation for nested attributes. Arrays are zero-indexed.  Fields may appear more than once in an array of causes due to fields having multiple errors. Optional.  Examples:   "name" - the field "name" on the current resource   "items[0].name" - the field "name" on the first array entry in "items"|
|message|string|false|A human-readable description of the cause of the error.  This field may be presented as-is to a reader.|
|reason|string|false|A machine-readable description of the cause of the error. If this value is empty there is no information available.|

<h2 id="tocSv1.statusdetails">v1.StatusDetails</h2>

<a id="schemav1.statusdetails"></a>

```json
{
  "causes": [
    {
      "field": "string",
      "message": "string",
      "reason": "string"
    }
  ],
  "group": "string",
  "kind": "string",
  "name": "string",
  "retryAfterSeconds": 0,
  "uid": "string"
}
```

### Properties

*StatusDetails is a set of additional properties that MAY be set by the server to provide additional information about a response. The Reason field of a Status object defines what attributes will be set. Clients must ignore fields that do not match the defined type of each attribute, and should assume that any attribute may be empty, invalid, or under defined.*

|Name|Type|Required|Description|
|---|---|---|---|
|causes|[[v1.StatusCause](#schemav1.statuscause)]|false|The Causes array includes more details associated with the StatusReason failure. Not all StatusReasons may provide detailed causes.|
|group|string|false|The group attribute of the resource associated with the status StatusReason.|
|kind|string|false|The kind attribute of the resource associated with the status StatusReason. On some operations may differ from the requested resource Kind. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|name|string|false|The name attribute of the resource associated with the status StatusReason (when there is a single name which can be described).|
|retryAfterSeconds|integer(int32)|false|If specified, the time in seconds before the operation should be retried. Some errors may indicate the client must take an alternate action - for those errors this field may indicate how long to wait before taking the alternate action.|
|uid|string|false|UID of the resource. (when there is a single resource which can be described). More info: http://kubernetes.io/docs/user-guide/identifiers#uids|

<h2 id="tocSv1.timer">v1.Timer</h2>

<a id="schemav1.timer"></a>

```json
{
  "hpet": {
    "present": true,
    "tickPolicy": "string"
  },
  "hyperv": {
    "present": true
  },
  "kvm": {
    "present": true
  },
  "pit": {
    "present": true,
    "tickPolicy": "string"
  },
  "rtc": {
    "present": true,
    "tickPolicy": "string",
    "track": "string"
  }
}
```

### Properties

*Represents all available timers in a vm*

|Name|Type|Required|Description|
|---|---|---|---|
|hpet|[v1.HPETTimer](#schemav1.hpettimer)|false|No description|
|hyperv|[v1.HypervTimer](#schemav1.hypervtimer)|false|No description|
|kvm|[v1.KVMTimer](#schemav1.kvmtimer)|false|No description|
|pit|[v1.PITTimer](#schemav1.pittimer)|false|No description|
|rtc|[v1.RTCTimer](#schemav1.rtctimer)|false|No description|

<h2 id="tocSv1.vmreplicasetcondition">v1.VMReplicaSetCondition</h2>

<a id="schemav1.vmreplicasetcondition"></a>

```json
{
  "lastProbeTime": "string",
  "lastTransitionTime": "string",
  "message": "string",
  "reason": "string",
  "status": "string",
  "type": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|lastProbeTime|string|false|No description|
|lastTransitionTime|string|false|No description|
|message|string|false|No description|
|reason|string|false|No description|
|status|string|true|No description|
|type|string|true|No description|

<h2 id="tocSv1.vmreplicasetspec">v1.VMReplicaSetSpec</h2>

<a id="schemav1.vmreplicasetspec"></a>

```json
{
  "paused": true,
  "replicas": 0,
  "selector": {
    "matchExpressions": [
      {
        "key": "string",
        "operator": "string",
        "values": [
          "string"
        ]
      }
    ],
    "matchLabels": {}
  },
  "template": {
    "metadata": {
      "annotations": {},
      "clusterName": "string",
      "creationTimestamp": "string",
      "deletionGracePeriodSeconds": 0,
      "deletionTimestamp": "string",
      "finalizers": [
        "string"
      ],
      "generateName": "string",
      "generation": 0,
      "initializers": {
        "pending": [
          {
            "name": "string"
          }
        ],
        "result": {
          "apiVersion": "string",
          "code": 0,
          "details": {
            "causes": [
              {
                "field": "string",
                "message": "string",
                "reason": "string"
              }
            ],
            "group": "string",
            "kind": "string",
            "name": "string",
            "retryAfterSeconds": 0,
            "uid": "string"
          },
          "kind": "string",
          "message": "string",
          "metadata": {
            "continue": "string",
            "resourceVersion": "string",
            "selfLink": "string"
          },
          "reason": "string",
          "status": "string"
        }
      },
      "labels": {},
      "name": "string",
      "namespace": "string",
      "ownerReferences": [
        {
          "apiVersion": "string",
          "blockOwnerDeletion": true,
          "controller": true,
          "kind": "string",
          "name": "string",
          "uid": "string"
        }
      ],
      "resourceVersion": "string",
      "selfLink": "string",
      "uid": "string"
    },
    "spec": {
      "affinity": {
        "nodeAffinity": {
          "preferredDuringSchedulingIgnoredDuringExecution": [
            {
              "preference": {
                "matchExpressions": [
                  {
                    "key": "string",
                    "operator": "string",
                    "values": []
                  }
                ]
              },
              "weight": 0
            }
          ],
          "requiredDuringSchedulingIgnoredDuringExecution": {
            "nodeSelectorTerms": [
              {
                "matchExpressions": [
                  {
                    "key": "string",
                    "operator": "string",
                    "values": []
                  }
                ]
              }
            ]
          }
        }
      },
      "domain": {
        "clock": {
          "timer": {
            "hpet": {
              "present": true,
              "tickPolicy": "string"
            },
            "hyperv": {
              "present": true
            },
            "kvm": {
              "present": true
            },
            "pit": {
              "present": true,
              "tickPolicy": "string"
            },
            "rtc": {
              "present": true,
              "tickPolicy": "string",
              "track": "string"
            }
          },
          "timezone": null,
          "utc": {
            "offsetSeconds": 0
          }
        },
        "cpu": {
          "cores": 0
        },
        "devices": {
          "disks": [
            {
              "cdrom": {
                "bus": "string",
                "readonly": true,
                "tray": "string"
              },
              "disk": {
                "bus": "string",
                "readonly": true
              },
              "floppy": {
                "readonly": true,
                "tray": "string"
              },
              "lun": {
                "bus": "string",
                "readonly": true
              },
              "name": "string",
              "volumeName": "string"
            }
          ],
          "watchdog": {
            "i6300esb": {
              "action": "string"
            },
            "name": "string"
          }
        },
        "features": {
          "acpi": {
            "enabled": true
          },
          "apic": {
            "enabled": true,
            "endOfInterrupt": true
          },
          "hyperv": {
            "relaxed": {
              "enabled": true
            },
            "reset": {
              "enabled": true
            },
            "runtime": {
              "enabled": true
            },
            "spinlocks": {
              "enabled": true,
              "spinlocks": 0
            },
            "synic": {
              "enabled": true
            },
            "synictimer": {
              "enabled": true
            },
            "vapic": {
              "enabled": true
            },
            "vendorid": {
              "enabled": true,
              "vendorid": "string"
            },
            "vpindex": {
              "enabled": true
            }
          }
        },
        "firmware": {
          "uuid": "string"
        },
        "machine": {
          "type": "string"
        },
        "resources": {
          "limits": {},
          "requests": {}
        }
      },
      "nodeSelector": {},
      "terminationGracePeriodSeconds": 0,
      "volumes": [
        {
          "cloudInitNoCloud": {
            "secretRef": {
              "name": "string"
            },
            "userData": "string",
            "userDataBase64": "string"
          },
          "emptyDisk": {
            "capacity": "string"
          },
          "ephemeral": {
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            }
          },
          "name": "string",
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          },
          "registryDisk": {
            "image": "string",
            "imagePullSecret": "string"
          }
        }
      ]
    }
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|paused|boolean|false|Indicates that the replica set is paused. +optional|
|replicas|integer(int32)|false|Number of desired pods. This is a pointer to distinguish between explicit zero and not specified. Defaults to 1. +optional|
|selector|[v1.LabelSelector](#schemav1.labelselector)|false|No description|
|template|[v1.VMTemplateSpec](#schemav1.vmtemplatespec)|true|No description|

<h2 id="tocSv1.vmreplicasetstatus">v1.VMReplicaSetStatus</h2>

<a id="schemav1.vmreplicasetstatus"></a>

```json
{
  "conditions": [
    {
      "lastProbeTime": "string",
      "lastTransitionTime": "string",
      "message": "string",
      "reason": "string",
      "status": "string",
      "type": "string"
    }
  ],
  "readyReplicas": 0,
  "replicas": 0
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|conditions|[[v1.VMReplicaSetCondition](#schemav1.vmreplicasetcondition)]|false|No description|
|readyReplicas|integer(int32)|false|The number of ready replicas for this replica set. +optional|
|replicas|integer(int32)|false|Total number of non-terminated pods targeted by this deployment (their labels match the selector). +optional|

<h2 id="tocSv1.vmtemplatespec">v1.VMTemplateSpec</h2>

<a id="schemav1.vmtemplatespec"></a>

```json
{
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|metadata|[v1.ObjectMeta](#schemav1.objectmeta)|false|No description|
|spec|[v1.VirtualMachineSpec](#schemav1.virtualmachinespec)|false|No description|

<h2 id="tocSv1.virtualmachine">v1.VirtualMachine</h2>

<a id="schemav1.virtualmachine"></a>

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "affinity": {
      "nodeAffinity": {
        "preferredDuringSchedulingIgnoredDuringExecution": [
          {
            "preference": {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            },
            "weight": 0
          }
        ],
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [
            {
              "matchExpressions": [
                {
                  "key": "string",
                  "operator": "string",
                  "values": [
                    "string"
                  ]
                }
              ]
            }
          ]
        }
      }
    },
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "nodeSelector": {},
    "terminationGracePeriodSeconds": 0,
    "volumes": [
      {
        "cloudInitNoCloud": {
          "secretRef": {
            "name": "string"
          },
          "userData": "string",
          "userDataBase64": "string"
        },
        "emptyDisk": {
          "capacity": "string"
        },
        "ephemeral": {
          "persistentVolumeClaim": {
            "claimName": "string",
            "readOnly": true
          }
        },
        "name": "string",
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        },
        "registryDisk": {
          "image": "string",
          "imagePullSecret": "string"
        }
      }
    ]
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "interfaces": [
      {
        "ipAddress": "string",
        "mac": "string"
      }
    ],
    "nodeName": "string",
    "phase": "string"
  }
}
```

### Properties

*VirtualMachine is *the* VM Definition. It represents a virtual machine in the runtime environment of kubernetes.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ObjectMeta](#schemav1.objectmeta)|false|No description|
|spec|[v1.VirtualMachineSpec](#schemav1.virtualmachinespec)|false|No description|
|status|[v1.VirtualMachineStatus](#schemav1.virtualmachinestatus)|false|No description|

<h2 id="tocSv1.virtualmachinecondition">v1.VirtualMachineCondition</h2>

<a id="schemav1.virtualmachinecondition"></a>

```json
{
  "lastProbeTime": "string",
  "lastTransitionTime": "string",
  "message": "string",
  "reason": "string",
  "status": "string",
  "type": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|lastProbeTime|string|false|No description|
|lastTransitionTime|string|false|No description|
|message|string|false|No description|
|reason|string|false|No description|
|status|string|true|No description|
|type|string|true|No description|

<h2 id="tocSv1.virtualmachinelist">v1.VirtualMachineList</h2>

<a id="schemav1.virtualmachinelist"></a>

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "interfaces": [
          {
            "ipAddress": "string",
            "mac": "string"
          }
        ],
        "nodeName": "string",
        "phase": "string"
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

### Properties

*VirtualMachineList is a list of VirtualMachines*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|items|[[v1.VirtualMachine](#schemav1.virtualmachine)]|true|No description|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ListMeta](#schemav1.listmeta)|false|No description|

<h2 id="tocSv1.virtualmachinenetworkinterface">v1.VirtualMachineNetworkInterface</h2>

<a id="schemav1.virtualmachinenetworkinterface"></a>

```json
{
  "ipAddress": "string",
  "mac": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|ipAddress|string|false|IP address of a Virtual Machine interface|
|mac|string|false|Hardware address of a Virtual Machine interface|

<h2 id="tocSv1.virtualmachinepreset">v1.VirtualMachinePreset</h2>

<a id="schemav1.virtualmachinepreset"></a>

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "domain": {
      "clock": {
        "timer": {
          "hpet": {
            "present": true,
            "tickPolicy": "string"
          },
          "hyperv": {
            "present": true
          },
          "kvm": {
            "present": true
          },
          "pit": {
            "present": true,
            "tickPolicy": "string"
          },
          "rtc": {
            "present": true,
            "tickPolicy": "string",
            "track": "string"
          }
        },
        "timezone": null,
        "utc": {
          "offsetSeconds": 0
        }
      },
      "cpu": {
        "cores": 0
      },
      "devices": {
        "disks": [
          {
            "cdrom": {
              "bus": "string",
              "readonly": true,
              "tray": "string"
            },
            "disk": {
              "bus": "string",
              "readonly": true
            },
            "floppy": {
              "readonly": true,
              "tray": "string"
            },
            "lun": {
              "bus": "string",
              "readonly": true
            },
            "name": "string",
            "volumeName": "string"
          }
        ],
        "watchdog": {
          "i6300esb": {
            "action": "string"
          },
          "name": "string"
        }
      },
      "features": {
        "acpi": {
          "enabled": true
        },
        "apic": {
          "enabled": true,
          "endOfInterrupt": true
        },
        "hyperv": {
          "relaxed": {
            "enabled": true
          },
          "reset": {
            "enabled": true
          },
          "runtime": {
            "enabled": true
          },
          "spinlocks": {
            "enabled": true,
            "spinlocks": 0
          },
          "synic": {
            "enabled": true
          },
          "synictimer": {
            "enabled": true
          },
          "vapic": {
            "enabled": true
          },
          "vendorid": {
            "enabled": true,
            "vendorid": "string"
          },
          "vpindex": {
            "enabled": true
          }
        }
      },
      "firmware": {
        "uuid": "string"
      },
      "machine": {
        "type": "string"
      },
      "resources": {
        "limits": {},
        "requests": {}
      }
    },
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    }
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ObjectMeta](#schemav1.objectmeta)|false|No description|
|spec|[v1.VirtualMachinePresetSpec](#schemav1.virtualmachinepresetspec)|false|No description|

<h2 id="tocSv1.virtualmachinepresetlist">v1.VirtualMachinePresetList</h2>

<a id="schemav1.virtualmachinepresetlist"></a>

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        }
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

### Properties

*VirtualMachinePresetList is a list of VirtualMachinePresets*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|items|[[v1.VirtualMachinePreset](#schemav1.virtualmachinepreset)]|true|No description|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ListMeta](#schemav1.listmeta)|false|No description|

<h2 id="tocSv1.virtualmachinepresetspec">v1.VirtualMachinePresetSpec</h2>

<a id="schemav1.virtualmachinepresetspec"></a>

```json
{
  "domain": {
    "clock": {
      "timer": {
        "hpet": {
          "present": true,
          "tickPolicy": "string"
        },
        "hyperv": {
          "present": true
        },
        "kvm": {
          "present": true
        },
        "pit": {
          "present": true,
          "tickPolicy": "string"
        },
        "rtc": {
          "present": true,
          "tickPolicy": "string",
          "track": "string"
        }
      },
      "timezone": null,
      "utc": {
        "offsetSeconds": 0
      }
    },
    "cpu": {
      "cores": 0
    },
    "devices": {
      "disks": [
        {
          "cdrom": {
            "bus": "string",
            "readonly": true,
            "tray": "string"
          },
          "disk": {
            "bus": "string",
            "readonly": true
          },
          "floppy": {
            "readonly": true,
            "tray": "string"
          },
          "lun": {
            "bus": "string",
            "readonly": true
          },
          "name": "string",
          "volumeName": "string"
        }
      ],
      "watchdog": {
        "i6300esb": {
          "action": "string"
        },
        "name": "string"
      }
    },
    "features": {
      "acpi": {
        "enabled": true
      },
      "apic": {
        "enabled": true,
        "endOfInterrupt": true
      },
      "hyperv": {
        "relaxed": {
          "enabled": true
        },
        "reset": {
          "enabled": true
        },
        "runtime": {
          "enabled": true
        },
        "spinlocks": {
          "enabled": true,
          "spinlocks": 0
        },
        "synic": {
          "enabled": true
        },
        "synictimer": {
          "enabled": true
        },
        "vapic": {
          "enabled": true
        },
        "vendorid": {
          "enabled": true,
          "vendorid": "string"
        },
        "vpindex": {
          "enabled": true
        }
      }
    },
    "firmware": {
      "uuid": "string"
    },
    "machine": {
      "type": "string"
    },
    "resources": {
      "limits": {},
      "requests": {}
    }
  },
  "selector": {
    "matchExpressions": [
      {
        "key": "string",
        "operator": "string",
        "values": [
          "string"
        ]
      }
    ],
    "matchLabels": {}
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|domain|[v1.DomainSpec](#schemav1.domainspec)|false|No description|
|selector|[v1.LabelSelector](#schemav1.labelselector)|true|No description|

<h2 id="tocSv1.virtualmachinereplicaset">v1.VirtualMachineReplicaSet</h2>

<a id="schemav1.virtualmachinereplicaset"></a>

```json
{
  "apiVersion": "string",
  "kind": "string",
  "metadata": {
    "annotations": {},
    "clusterName": "string",
    "creationTimestamp": "string",
    "deletionGracePeriodSeconds": 0,
    "deletionTimestamp": "string",
    "finalizers": [
      "string"
    ],
    "generateName": "string",
    "generation": 0,
    "initializers": {
      "pending": [
        {
          "name": "string"
        }
      ],
      "result": {
        "apiVersion": "string",
        "code": 0,
        "details": {
          "causes": [
            {
              "field": "string",
              "message": "string",
              "reason": "string"
            }
          ],
          "group": "string",
          "kind": "string",
          "name": "string",
          "retryAfterSeconds": 0,
          "uid": "string"
        },
        "kind": "string",
        "message": "string",
        "metadata": {
          "continue": "string",
          "resourceVersion": "string",
          "selfLink": "string"
        },
        "reason": "string",
        "status": "string"
      }
    },
    "labels": {},
    "name": "string",
    "namespace": "string",
    "ownerReferences": [
      {
        "apiVersion": "string",
        "blockOwnerDeletion": true,
        "controller": true,
        "kind": "string",
        "name": "string",
        "uid": "string"
      }
    ],
    "resourceVersion": "string",
    "selfLink": "string",
    "uid": "string"
  },
  "spec": {
    "paused": true,
    "replicas": 0,
    "selector": {
      "matchExpressions": [
        {
          "key": "string",
          "operator": "string",
          "values": [
            "string"
          ]
        }
      ],
      "matchLabels": {}
    },
    "template": {
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "affinity": {
          "nodeAffinity": {
            "preferredDuringSchedulingIgnoredDuringExecution": [
              {
                "preference": {
                  "matchExpressions": [
                    {}
                  ]
                },
                "weight": 0
              }
            ],
            "requiredDuringSchedulingIgnoredDuringExecution": {
              "nodeSelectorTerms": [
                {
                  "matchExpressions": [
                    {}
                  ]
                }
              ]
            }
          }
        },
        "domain": {
          "clock": {
            "timer": {
              "hpet": {
                "present": true,
                "tickPolicy": "string"
              },
              "hyperv": {
                "present": true
              },
              "kvm": {
                "present": true
              },
              "pit": {
                "present": true,
                "tickPolicy": "string"
              },
              "rtc": {
                "present": true,
                "tickPolicy": "string",
                "track": "string"
              }
            },
            "timezone": null,
            "utc": {
              "offsetSeconds": 0
            }
          },
          "cpu": {
            "cores": 0
          },
          "devices": {
            "disks": [
              {
                "cdrom": {
                  "bus": "string",
                  "readonly": true,
                  "tray": "string"
                },
                "disk": {
                  "bus": "string",
                  "readonly": true
                },
                "floppy": {
                  "readonly": true,
                  "tray": "string"
                },
                "lun": {
                  "bus": "string",
                  "readonly": true
                },
                "name": "string",
                "volumeName": "string"
              }
            ],
            "watchdog": {
              "i6300esb": {
                "action": "string"
              },
              "name": "string"
            }
          },
          "features": {
            "acpi": {
              "enabled": true
            },
            "apic": {
              "enabled": true,
              "endOfInterrupt": true
            },
            "hyperv": {
              "relaxed": {
                "enabled": true
              },
              "reset": {
                "enabled": true
              },
              "runtime": {
                "enabled": true
              },
              "spinlocks": {
                "enabled": true,
                "spinlocks": 0
              },
              "synic": {
                "enabled": true
              },
              "synictimer": {
                "enabled": true
              },
              "vapic": {
                "enabled": true
              },
              "vendorid": {
                "enabled": true,
                "vendorid": "string"
              },
              "vpindex": {
                "enabled": true
              }
            }
          },
          "firmware": {
            "uuid": "string"
          },
          "machine": {
            "type": "string"
          },
          "resources": {
            "limits": {},
            "requests": {}
          }
        },
        "nodeSelector": {},
        "terminationGracePeriodSeconds": 0,
        "volumes": [
          {
            "cloudInitNoCloud": {
              "secretRef": {
                "name": "string"
              },
              "userData": "string",
              "userDataBase64": "string"
            },
            "emptyDisk": {
              "capacity": "string"
            },
            "ephemeral": {
              "persistentVolumeClaim": {
                "claimName": "string",
                "readOnly": true
              }
            },
            "name": "string",
            "persistentVolumeClaim": {
              "claimName": "string",
              "readOnly": true
            },
            "registryDisk": {
              "image": "string",
              "imagePullSecret": "string"
            }
          }
        ]
      }
    }
  },
  "status": {
    "conditions": [
      {
        "lastProbeTime": "string",
        "lastTransitionTime": "string",
        "message": "string",
        "reason": "string",
        "status": "string",
        "type": "string"
      }
    ],
    "readyReplicas": 0,
    "replicas": 0
  }
}
```

### Properties

*VM is *the* VM Definition. It represents a virtual machine in the runtime environment of kubernetes.*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ObjectMeta](#schemav1.objectmeta)|false|No description|
|spec|[v1.VMReplicaSetSpec](#schemav1.vmreplicasetspec)|false|No description|
|status|[v1.VMReplicaSetStatus](#schemav1.vmreplicasetstatus)|false|No description|

<h2 id="tocSv1.virtualmachinereplicasetlist">v1.VirtualMachineReplicaSetList</h2>

<a id="schemav1.virtualmachinereplicasetlist"></a>

```json
{
  "apiVersion": "string",
  "items": [
    {
      "apiVersion": "string",
      "kind": "string",
      "metadata": {
        "annotations": {},
        "clusterName": "string",
        "creationTimestamp": "string",
        "deletionGracePeriodSeconds": 0,
        "deletionTimestamp": "string",
        "finalizers": [
          "string"
        ],
        "generateName": "string",
        "generation": 0,
        "initializers": {
          "pending": [
            {
              "name": "string"
            }
          ],
          "result": {
            "apiVersion": "string",
            "code": 0,
            "details": {
              "causes": [
                {
                  "field": "string",
                  "message": "string",
                  "reason": "string"
                }
              ],
              "group": "string",
              "kind": "string",
              "name": "string",
              "retryAfterSeconds": 0,
              "uid": "string"
            },
            "kind": "string",
            "message": "string",
            "metadata": {
              "continue": "string",
              "resourceVersion": "string",
              "selfLink": "string"
            },
            "reason": "string",
            "status": "string"
          }
        },
        "labels": {},
        "name": "string",
        "namespace": "string",
        "ownerReferences": [
          {
            "apiVersion": "string",
            "blockOwnerDeletion": true,
            "controller": true,
            "kind": "string",
            "name": "string",
            "uid": "string"
          }
        ],
        "resourceVersion": "string",
        "selfLink": "string",
        "uid": "string"
      },
      "spec": {
        "paused": true,
        "replicas": 0,
        "selector": {
          "matchExpressions": [
            {
              "key": "string",
              "operator": "string",
              "values": [
                "string"
              ]
            }
          ],
          "matchLabels": {}
        },
        "template": {
          "metadata": {
            "annotations": {},
            "clusterName": "string",
            "creationTimestamp": "string",
            "deletionGracePeriodSeconds": 0,
            "deletionTimestamp": "string",
            "finalizers": [
              "string"
            ],
            "generateName": "string",
            "generation": 0,
            "initializers": {
              "pending": [
                {
                  "name": "string"
                }
              ],
              "result": {
                "apiVersion": "string",
                "code": 0,
                "details": {
                  "causes": [
                    {}
                  ],
                  "group": "string",
                  "kind": "string",
                  "name": "string",
                  "retryAfterSeconds": 0,
                  "uid": "string"
                },
                "kind": "string",
                "message": "string",
                "metadata": {
                  "continue": "string",
                  "resourceVersion": "string",
                  "selfLink": "string"
                },
                "reason": "string",
                "status": "string"
              }
            },
            "labels": {},
            "name": "string",
            "namespace": "string",
            "ownerReferences": [
              {
                "apiVersion": "string",
                "blockOwnerDeletion": true,
                "controller": true,
                "kind": "string",
                "name": "string",
                "uid": "string"
              }
            ],
            "resourceVersion": "string",
            "selfLink": "string",
            "uid": "string"
          },
          "spec": {
            "affinity": {
              "nodeAffinity": {
                "preferredDuringSchedulingIgnoredDuringExecution": [
                  {
                    "preference": {},
                    "weight": 0
                  }
                ],
                "requiredDuringSchedulingIgnoredDuringExecution": {
                  "nodeSelectorTerms": [
                    {}
                  ]
                }
              }
            },
            "domain": {
              "clock": {
                "timer": {
                  "hpet": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "hyperv": {
                    "present": true
                  },
                  "kvm": {
                    "present": true
                  },
                  "pit": {
                    "present": true,
                    "tickPolicy": "string"
                  },
                  "rtc": {
                    "present": true,
                    "tickPolicy": "string",
                    "track": "string"
                  }
                },
                "timezone": null,
                "utc": {
                  "offsetSeconds": 0
                }
              },
              "cpu": {
                "cores": 0
              },
              "devices": {
                "disks": [
                  {
                    "cdrom": {},
                    "disk": {},
                    "floppy": {},
                    "lun": {},
                    "name": "string",
                    "volumeName": "string"
                  }
                ],
                "watchdog": {
                  "i6300esb": {
                    "action": "string"
                  },
                  "name": "string"
                }
              },
              "features": {
                "acpi": {
                  "enabled": true
                },
                "apic": {
                  "enabled": true,
                  "endOfInterrupt": true
                },
                "hyperv": {
                  "relaxed": {
                    "enabled": true
                  },
                  "reset": {
                    "enabled": true
                  },
                  "runtime": {
                    "enabled": true
                  },
                  "spinlocks": {
                    "enabled": true,
                    "spinlocks": 0
                  },
                  "synic": {
                    "enabled": true
                  },
                  "synictimer": {
                    "enabled": true
                  },
                  "vapic": {
                    "enabled": true
                  },
                  "vendorid": {
                    "enabled": true,
                    "vendorid": "string"
                  },
                  "vpindex": {
                    "enabled": true
                  }
                }
              },
              "firmware": {
                "uuid": "string"
              },
              "machine": {
                "type": "string"
              },
              "resources": {
                "limits": {},
                "requests": {}
              }
            },
            "nodeSelector": {},
            "terminationGracePeriodSeconds": 0,
            "volumes": [
              {
                "cloudInitNoCloud": {
                  "secretRef": {
                    "name": "string"
                  },
                  "userData": "string",
                  "userDataBase64": "string"
                },
                "emptyDisk": {
                  "capacity": "string"
                },
                "ephemeral": {
                  "persistentVolumeClaim": {
                    "claimName": "string",
                    "readOnly": true
                  }
                },
                "name": "string",
                "persistentVolumeClaim": {
                  "claimName": "string",
                  "readOnly": true
                },
                "registryDisk": {
                  "image": "string",
                  "imagePullSecret": "string"
                }
              }
            ]
          }
        }
      },
      "status": {
        "conditions": [
          {
            "lastProbeTime": "string",
            "lastTransitionTime": "string",
            "message": "string",
            "reason": "string",
            "status": "string",
            "type": "string"
          }
        ],
        "readyReplicas": 0,
        "replicas": 0
      }
    }
  ],
  "kind": "string",
  "metadata": {
    "continue": "string",
    "resourceVersion": "string",
    "selfLink": "string"
  }
}
```

### Properties

*VMList is a list of VMs*

|Name|Type|Required|Description|
|---|---|---|---|
|apiVersion|string|false|APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#resources|
|items|[[v1.VirtualMachineReplicaSet](#schemav1.virtualmachinereplicaset)]|true|No description|
|kind|string|false|Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/api-conventions.md#types-kinds|
|metadata|[v1.ListMeta](#schemav1.listmeta)|false|No description|

<h2 id="tocSv1.virtualmachinespec">v1.VirtualMachineSpec</h2>

<a id="schemav1.virtualmachinespec"></a>

```json
{
  "affinity": {
    "nodeAffinity": {
      "preferredDuringSchedulingIgnoredDuringExecution": [
        {
          "preference": {
            "matchExpressions": [
              {
                "key": "string",
                "operator": "string",
                "values": [
                  "string"
                ]
              }
            ]
          },
          "weight": 0
        }
      ],
      "requiredDuringSchedulingIgnoredDuringExecution": {
        "nodeSelectorTerms": [
          {
            "matchExpressions": [
              {
                "key": "string",
                "operator": "string",
                "values": [
                  "string"
                ]
              }
            ]
          }
        ]
      }
    }
  },
  "domain": {
    "clock": {
      "timer": {
        "hpet": {
          "present": true,
          "tickPolicy": "string"
        },
        "hyperv": {
          "present": true
        },
        "kvm": {
          "present": true
        },
        "pit": {
          "present": true,
          "tickPolicy": "string"
        },
        "rtc": {
          "present": true,
          "tickPolicy": "string",
          "track": "string"
        }
      },
      "timezone": null,
      "utc": {
        "offsetSeconds": 0
      }
    },
    "cpu": {
      "cores": 0
    },
    "devices": {
      "disks": [
        {
          "cdrom": {
            "bus": "string",
            "readonly": true,
            "tray": "string"
          },
          "disk": {
            "bus": "string",
            "readonly": true
          },
          "floppy": {
            "readonly": true,
            "tray": "string"
          },
          "lun": {
            "bus": "string",
            "readonly": true
          },
          "name": "string",
          "volumeName": "string"
        }
      ],
      "watchdog": {
        "i6300esb": {
          "action": "string"
        },
        "name": "string"
      }
    },
    "features": {
      "acpi": {
        "enabled": true
      },
      "apic": {
        "enabled": true,
        "endOfInterrupt": true
      },
      "hyperv": {
        "relaxed": {
          "enabled": true
        },
        "reset": {
          "enabled": true
        },
        "runtime": {
          "enabled": true
        },
        "spinlocks": {
          "enabled": true,
          "spinlocks": 0
        },
        "synic": {
          "enabled": true
        },
        "synictimer": {
          "enabled": true
        },
        "vapic": {
          "enabled": true
        },
        "vendorid": {
          "enabled": true,
          "vendorid": "string"
        },
        "vpindex": {
          "enabled": true
        }
      }
    },
    "firmware": {
      "uuid": "string"
    },
    "machine": {
      "type": "string"
    },
    "resources": {
      "limits": {},
      "requests": {}
    }
  },
  "nodeSelector": {},
  "terminationGracePeriodSeconds": 0,
  "volumes": [
    {
      "cloudInitNoCloud": {
        "secretRef": {
          "name": "string"
        },
        "userData": "string",
        "userDataBase64": "string"
      },
      "emptyDisk": {
        "capacity": "string"
      },
      "ephemeral": {
        "persistentVolumeClaim": {
          "claimName": "string",
          "readOnly": true
        }
      },
      "name": "string",
      "persistentVolumeClaim": {
        "claimName": "string",
        "readOnly": true
      },
      "registryDisk": {
        "image": "string",
        "imagePullSecret": "string"
      }
    }
  ]
}
```

### Properties

*VirtualMachineSpec is a description of a VirtualMachine.*

|Name|Type|Required|Description|
|---|---|---|---|
|affinity|[v1.Affinity](#schemav1.affinity)|false|No description|
|domain|[v1.DomainSpec](#schemav1.domainspec)|true|No description|
|nodeSelector|object|false|NodeSelector is a selector which must be true for the vm to fit on a node. Selector which must match a node's labels for the vm to be scheduled on that node. More info: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/ +optional|
|terminationGracePeriodSeconds|integer(int64)|false|Grace period observed after signalling a VM to stop after which the VM is force terminated.|
|volumes|[[v1.Volume](#schemav1.volume)]|false|List of volumes that can be mounted by disks belonging to the vm.|

<h2 id="tocSv1.virtualmachinestatus">v1.VirtualMachineStatus</h2>

<a id="schemav1.virtualmachinestatus"></a>

```json
{
  "conditions": [
    {
      "lastProbeTime": "string",
      "lastTransitionTime": "string",
      "message": "string",
      "reason": "string",
      "status": "string",
      "type": "string"
    }
  ],
  "interfaces": [
    {
      "ipAddress": "string",
      "mac": "string"
    }
  ],
  "nodeName": "string",
  "phase": "string"
}
```

### Properties

*VirtualMachineStatus represents information about the status of a VM. Status may trail the actual
state of a system.*

|Name|Type|Required|Description|
|---|---|---|---|
|conditions|[[v1.VirtualMachineCondition](#schemav1.virtualmachinecondition)]|false|Conditions are specific points in VM's pod runtime.|
|interfaces|[[v1.VirtualMachineNetworkInterface](#schemav1.virtualmachinenetworkinterface)]|false|Interfaces represent the details of available network interfaces.|
|nodeName|string|false|NodeName is the name where the VM is currently running.|
|phase|string|false|Phase is the status of the VM in kubernetes world. It is not the VM status, but partially correlates to it.|

<h2 id="tocSv1.volume">v1.Volume</h2>

<a id="schemav1.volume"></a>

```json
{
  "cloudInitNoCloud": {
    "secretRef": {
      "name": "string"
    },
    "userData": "string",
    "userDataBase64": "string"
  },
  "emptyDisk": {
    "capacity": "string"
  },
  "ephemeral": {
    "persistentVolumeClaim": {
      "claimName": "string",
      "readOnly": true
    }
  },
  "name": "string",
  "persistentVolumeClaim": {
    "claimName": "string",
    "readOnly": true
  },
  "registryDisk": {
    "image": "string",
    "imagePullSecret": "string"
  }
}
```

### Properties

*Volume represents a named volume in a vm.*

|Name|Type|Required|Description|
|---|---|---|---|
|cloudInitNoCloud|[v1.CloudInitNoCloudSource](#schemav1.cloudinitnocloudsource)|false|No description|
|emptyDisk|[v1.EmptyDiskSource](#schemav1.emptydisksource)|false|No description|
|ephemeral|[v1.EphemeralVolumeSource](#schemav1.ephemeralvolumesource)|false|No description|
|name|string|true|Volume's name. Must be a DNS_LABEL and unique within the vm. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names|
|persistentVolumeClaim|[v1.PersistentVolumeClaimVolumeSource](#schemav1.persistentvolumeclaimvolumesource)|false|No description|
|registryDisk|[v1.RegistryDiskSource](#schemav1.registrydisksource)|false|No description|

<h2 id="tocSv1.watchevent">v1.WatchEvent</h2>

<a id="schemav1.watchevent"></a>

```json
{
  "object": "string",
  "type": "string"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|object|string|true|No description|
|type|string|true|No description|

<h2 id="tocSv1.watchdog">v1.Watchdog</h2>

<a id="schemav1.watchdog"></a>

```json
{
  "i6300esb": {
    "action": "string"
  },
  "name": "string"
}
```

### Properties

*Named watchdog device*

|Name|Type|Required|Description|
|---|---|---|---|
|i6300esb|[v1.I6300ESBWatchdog](#schemav1.i6300esbwatchdog)|false|No description|
|name|string|true|Name of the watchdog|

