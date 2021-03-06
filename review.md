The [KubeVirt](https://github.com/kubevirt/kubevirt/) project provides extensions to Kubernetes via [custom resources](https://kubernetes.io/docs/concepts/api-extension/custom-resources/). These resources are a collection a API objects that defines a virtual machine within Kubernetes. Let’s take a look at the objects that are available.

KubeVirt top-level objects
==========================

Below is a list of the top level API objects and descriptions that KubeVirt provides.

-   VirtualMachine (vm\[s\]) - represents a virtual machine in the runtime environment of Kubernetes.

-   OfflineVirtualMachine (ovm\[s\]) - handles the virtual machines that are not running or are in a stopped state.

-   VirtualMachinePreset (vmpreset\[s\]) - is an extension to general VirtualMachine configuration behaving much like PodPresets from Kubernetes. When a VirtualMachine is created, any applicable VirtualMachinePresets will be applied to the existing spec for the VirtualMachine. This allows for re-use of common settings that should apply to multiple VirtualMachines.

-   VirtualMachineReplicaSet (vmrs\[s\]) - tries to ensures that a specified number of VirtualMachine replicas are running at any time.

There are other top-level objects which are lists of the above four: VirtualMachineList, OfflineVirtualMachineList, VirtualMachineReplicaSetList and VirtualMachinePresetList.

[DomainSpec](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_domainspec) is listed as a top-level object but is only used within all of the objects above. Currently the `DomainSpec` is a subset of what is configurable via [libvirt domain XML](https://libvirt.org/formatdomain.html).

VirtualMachine
--------------

First let’s use `kubectl` to retrieve a list of `VirtualMachine` objects.

    $ kubectl get vms -n nodejs-ex
    NAME      AGE
    mongodb   5d
    nodejs    5d

Just in case if you want to return the yaml definition of a `VirtualMachine` object here is an example.

    $ kubectl -o yaml get vms mongodb -n nodejs-ex
    apiVersion: kubevirt.io/v1alpha1
    kind: VirtualMachine
    ...output...

The first object we will annotate is `VirtualMachine`. The important sections `.spec` for `VirtualMachineSpec` and `.spec.domain` for `DomainSpec` will be annotated only in this section then referred to in the other object sections.

    apiVersion: kubevirt.io/v1alpha1
    kind: VirtualMachine
    metadata:
      annotations: {}
      labels: {}
      name: string
      namespace: string
    spec: {}

### Node Placement

Kubernetes has the ability to schedule a pod to specific nodes based on [affinity and anti-affinity](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#node-affinity-beta-feature) rules.

[Node affinity](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_nodeaffinity) is also possible with KubeVirt. To [constrain a virtual machine](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/assigning-vms-to-nodes?id=affinity-and-anti-affinity) to run on a node define a matching expressions using node labels.

      affinity:
        nodeAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
          - preference:
              matchExpressions:
              - key: string
                operator: string
                values:
                - string
            weight: 0
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: string
                operator: string
                values:
                - string

A virtual machine can also more easily be constrained by using [nodeSelector](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/assigning-vms-to-nodes?id=nodeselector) which is defined by node’s label and value. Here is an example

      nodeSelector:
        kubernetes.io/hostname: kn1.virtomation.com

### Clocks and Timers

Configures the [virtualize hardware](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=clock) clock provided by [QEMU](https://qemu.weilnetz.de/doc/qemu-doc.html#Debug_002fExpert-options).

      domain:
        clock:
          timezone: string
          utc:
            offsetSeconds: 0

The [timer](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=timers) defines the [type and policy attribute](https://libvirt.org/formatdomain.html#elementsTime) that determines what action is take when QEMU misses a deadline for injecting a tick to the guest.

      domain:
        clock:
          timer:
            hpet:
              present: true
              tickPolicy: string
            hyperv:
              present: true
            kvm:
              present: true
            pit:
              present: true
              tickPolicy: string
            rtc:
              present: true
              tickPolicy: string
              track: string

### CPU and Memory

The number of [CPU cores](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=cpu) a virtual machine will be assigned. [.spec.domain.cpu.cores](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_cpu) will not be used for scheduling use [.spec.domain.resources.requests.cpu](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_resourcerequirements) instead.

        cpu:
          cores: 1

There are two supported [resource limits and requests](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=resources-requests-and-limits): `cpu` and `memory`. A `.spec.domain.resources.requests.memory` should be defined to determine the allocation of memory provided to the virtual machine. These values will be used to in scheduling decisions.

        resources:
          limits: {}
          requests: {}

### Watchdog Devices

[.spec.domain.watchdog](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_watchdog) automaticaly triggers an action via [Libvirt](https://libvirt.org/formatdomain.html#elementsWatchdog) and [QEMU](https://qemu.weilnetz.de/doc/qemu-doc.html#Debug_002fExpert-options) when the virtual machine operating system hangs or crashes.

          watchdog:
            i6300esb:
              action: string
            name: string

### Features

After reviewing both Linux and Microsoft QEMU virtual machines managed by [Libvirt](https://libvirt.org/formatdomain.html#elementsFeatures) both \[acpi\] and [apic](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_featureapic) are enabled. The [hyperv](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_featurehyperv) features should be enabled only for Windows-based virtual machines. For additional information regarding features please visit the [virtual hardware configuration](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=features) in the kubevirt user guide.

        features:
          acpi:
            enabled: true
          apic:
            enabled: true
            endOfInterrupt: true
          hyperv:
            relaxed:
              enabled: true
            reset:
              enabled: true
            runtime:
              enabled: true
            spinlocks:
              enabled: true
              spinlocks: 0
            synic:
              enabled: true
            synictimer:
              enabled: true
            vapic:
              enabled: true
            vendorid:
              enabled: true
              vendorid: string
            vpindex:
              enabled: true

### QEMU Machine Type

[.spec.domain.machine.type](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/virtualized-hardware-configuration?id=machine-type) is the emulated machine architecture provided by [QEMU](https://qemu.weilnetz.de/doc/qemu-doc.html#Standard-options).

        machine:
          type: string

Here is an example how to retrieve the supported QEMU machine types.

    $ qemu-system-x86_64 --machine help
    Supported machines are:
    ...output...
    pc                   Standard PC (i440FX + PIIX, 1996) (alias of pc-i440fx-2.10)
    pc-i440fx-2.10       Standard PC (i440FX + PIIX, 1996) (default)
    ...output...
    q35                  Standard PC (Q35 + ICH9, 2009) (alias of pc-q35-2.10)
    pc-q35-2.10          Standard PC (Q35 + ICH9, 2009)

### Disks and Volumes

[.spec.domain.devices.disks](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_disk) configures a [QEMU](https://qemu.weilnetz.de/doc/qemu-doc.html#Block-device-options) type of [disk](https://libvirt.org/formatdomain.html#elementsDisks) to the virtual machine and assigns a specific [volume and its type to that disk](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/disks-and-volumes) via the `volumeName`.

        devices:
          disks:
          - cdrom:
              bus: string
              readonly: true
              tray: string
            disk:
              bus: string
              readonly: true
            floppy:
              readonly: true
              tray: string
            lun:
              bus: string
              readonly: true
            name: string
            volumeName: string

[cloudInitNoCloud](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_cloudinitnocloudsource) injects scripts and configuration into a virtual machine operating system. There are three different parameters that can be used to provide the cloud-init coniguration: `secretRef`, `userData` or `userDataBase64`.

See the user-guide for examples of how to use [.spec.volumes.cloudInitNoCloud](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/startup-scripts?id=cloud-init-examples).

      volumes:
      - cloudInitNoCloud:
          secretRef:
            name: string
          userData: string
          userDataBase64: string

An [emptyDisk volume](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/disks-and-volumes?id=emptydisk) creates an extra qcow2 disk that is created with the virtual machine. It will be removed if the `VirtualMachine` object is deleted.

        emptyDisk:
          capacity: string

[Ephemeral volume](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/disks-and-volumes?id=ephemeral) creates a temporary local copy on write image storage that will be discarded when the `VirtualMachine` is removed.

        ephemeral:
          persistentVolumeClaim:
            claimName: string
            readOnly: true
        name: string

[persistentVolumeClaim volume](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/disks-and-volumes?id=persistentvolumeclaim) persists after the `VirtualMachine` is deleted.

        persistentVolumeClaim:
          claimName: string
          readOnly: true

[registryDisk volume](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/disks-and-volumes?id=registrydisk) type uses a virtual machine disk that is stored in a container image registry.

        registryDisk:
          image: string
          imagePullSecret: string

### Virtual Machine Status

Once the `VirtualMachine` object has been created the [VirtualMachineStatus](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_virtualmachinestatus) will be available. [VirtualMachineStatus](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_virtualmachinestatus) can be used in automation tools such as Ansible to confirm running state, determine where a `VirtualMachine` is running via `nodeName` or the `ipAddress` of the virtual machine operating system.

    kubectl -o yaml get vm mongodb -n nodejs-ex

    # ...output...
    status:
      interfaces:
      - ipAddress: 10.244.2.7
      nodeName: kn2.virtomation.com
      phase: Running

Example using `--template` to retrieve the `.status.phase` of the `VirtualMachine`.

    kubectl get vm mongodb --template {{.status.phase}} -n nodejs-ex
    Running

### Examples

-   <https://github.com/kubevirt/kubevirt/blob/master/cluster/examples/vm-fedora.yaml>

-   <https://github.com/kubevirt/kubevirt/blob/master/cluster/examples/vm-windows.yaml>

OfflineVirtualMachine
---------------------

After reviewing KubeVirt objects I think that `OfflineVirtualMachine` should be used in most use-cases. It seems more persistent than the ephemeral nature of the `VirtualMachine` object. We will see in the annotation section that virtual machine power state can be easily controlled by changing `running` boolean value.

Just like `VirtualMachine` we can retrieve the `OfflineVirtualMachine` objects.

    $ kubectl get ovms -n nodejs-ex
    NAME      AGE
    mongodb   5d
    nodejs    5d

And display the object in yaml.

    $ kubectl -o yaml get ovms mongodb -n nodejs-ex
    apiVersion: kubevirt.io/v1alpha1
    kind: OfflineVirtualMachine
    metadata:
    ...output...

We continue by annotating `OfflineVirtualMachine` object.

    apiVersion: kubevirt.io/v1alpha1
    kind: OfflineVirtualMachine
    metadata:
      annotations: {}
      labels: {}
      name: string
      namespace: string
    spec:

### What is Running in OfflineVirtualMachine?

[.spec.running](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_offlinevirtualmachinespec) controls whether the associatied VirtualMachine object is created. In other words this changes the [power status](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/life-cycle?id=stopping-a-virtual-machine) of the virtual machine.

      running: true

This will create a `VirtualMachine` object which will instantiate and power on a virtual machine.

    kubectl patch offlinevirtualmachine mongodb --type merge -p '{"spec":{"running":true }}' -n nodejs-ex

This will delete the `VirtualMachine` object which will power off the virtual machine.

    kubectl patch offlinevirtualmachine mongodb --type merge -p '{"spec":{"running":false }}' -n nodejs-ex

### Offline Virtual Machine Status

Once the `OfflineVirtualMachine` object has been created the [OfflineVirtualMachineStatus](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_offlinevirtualmachinestatus) will be available. Like `VirtualMachineStatus` `OfflineVirtualMachineStatus` can be used for automation tools such as Ansible.

    kubectl -o yaml get ovms mongodb -n nodejs-ex

    # ...output...
    status:
      conditions:
      - lastProbeTime: null
        lastTransitionTime: 2018-04-18T19:52:18Z
        message: Created by OVM mongodb
        reason: Created by OVM mongodb
        status: "True"
        type: Running

Example using `--template` to retrieve the `.status.conditions[0].type` of `OfflineVirtualMachine`.

    kubectl get ovm mongodb --template "{{(index .status.conditions 0).type}}" -n nodejs-ex
    Running

### Examples

-   <https://github.com/kubevirt/demo/blob/master/manifests/vm.yaml>

VirtualMachineReplicaSet
------------------------

[VirtualMachineReplicaSet](http://www.kubevirt.io/user-guide/#/workloads/controllers/virtual-machine-replica-set) is great when you want to run multiple identical virtual machines.

Just like the other top-level objects we can retrieve `VirtualMachineReplicaSet`.

    $ kubectl get vmrs -n nodejs-ex
    NAME      AGE
    replica   1m

With the `replicas` parameter set to `2` the command below displays the two `VirtualMachine` objects that were created.

    $ kubectl get vms -n nodejs-ex
    NAME           AGE
    replicanmgjl   7m
    replicarjhdz   7m

### Pause rollout

The [.spec.paused](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_vmreplicasetspec) parameter if true pauses the deployment of the `VirtualMachineReplicaSet`.

      paused: true

### Replica quantity

The [.spec.replicas](http://www.kubevirt.io/user-guide/#/workloads/controllers/virtual-machine-replica-set?id=how-to-use-a-virtualmachinereplicaset) number of `VirtualMachine` objects that should be created.

      replicas: 0

The [selector](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_labelselector) must be defined and match labels defined in the template. It is used by the controller to keep track of managed virtual machines.

      selector:
        matchExpressions:
        - key: string
          operator: string
          values:
          - string
        matchLabels: {}

### [Virtual Machine Template Spec](http://www.kubevirt.io/user-guide/#/workloads/controllers/virtual-machine-replica-set?id=how-to-use-a-virtualmachinereplicaset)

The `VMTemplateSpec` is the definition of a `VirtualMachine` objects that will be created.

In the `VirtualMachine` section the `.spec` `VirtualMachineSpec` describes the available parameters for that object.

      template:
        metadata:
          annotations: {}
          labels: {}
          name: string
          namespace: string
        spec: {}

### Replica Status

Like the other objects we already have discussed [VMReplicaSetStatus](http://www.kubevirt.io/api-reference/v0.4.1/definitions.html#_v1_vmreplicasetstatus) is an important object to use for automation.

    status:
      readyReplicas: 0
      replicas: 0

Example using `--template` to retrieve the `.status.readyReplicas` and `.status.replicas` of `VirtualMachineReplicaSet`.

    $ kubectl get vmrs replica --template "{{.status.readyReplicas}}" -n nodejs-ex
    2
    $ kubectl get vmrs replica --template "{{.status.replicas}}" -n nodejs-ex
    2

### Examples

-   <https://github.com/kubevirt/kubevirt/blob/master/cluster/examples/vm-replicaset-cirros.yaml>

VirtualMachinePreset
--------------------

This is used to define a `DomainSpec` that can be used for multiple virtual machines.

To configure a `DomainSpec` for multiple `VirtualMachine` objects the `selector` defines which `VirtualMachine` the `VirtualMachinePreset` should be applied to.

    $ kubectl get vmpreset -n nodejs-ex
    NAME       AGE
    m1.small   17s

### Domain Spec

See the `VirtualMachine` section above for annotated details of the `DomainSpec` object.

    spec:
      domain: {}

### Preset Selector

The [selector](http://www.kubevirt.io/user-guide/#/workloads/virtual-machines/presets?id=virtalmachine-selector) is optional but if not defined will be applied to all `VirtualMachine` objects; which is probably not the intended purpose so I recommend always including a selector.

      selector:
        matchExpressions:
        - key: string
          operator: string
          values:
          - string
        matchLabels: {}

### Examples

-   <https://github.com/kubevirt/kubevirt/blob/master/cluster/examples/vm-preset-small.yaml>

We provided an annotated view into the KubeVirt objects - VirtualMachine, OfflineVirtualMachine, VirtualMachineReplicaSet and VirtualMachienPreset. Hopefully this will help a user of KubeVirt to understand the options and parameters that are currently available when creating a virtual machine on Kubernetes.
