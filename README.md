OPNsense: Dashboard
===================

An Ansible role that configures some basic settings for the opnSense dashboard.

Requirements
------------

This role requires the `lxml` python package to be installed on the host system.

Role Variables
--------------

|                   Variable                    |      Type      |                                            Description                                            |
| :-------------------------------------------: | :------------: | :-----------------------------------------------------------------------------------------------: |
|          opnsense_dashboard_columns           |     `int`      |                        The number of columns to display on the dashboard.                         |
|       opnsense_dashboard_traphic_graph        |    `string`    |            Comma separated list of interfaces to display in the traphic graph widget.             |
|      opnsense_dashboard_widget_sequence       | `list(object)` |                        List of objects that contain widget configurations.                        |
|  opnsense_dashboard_widget_sequence[].widget  |    `string     |                               The actual name of the widget itself.                               |
| opnsense_dashboard_widget_sequence[].position |    `string`    |                                Positioning number for the widget.                                 |
|  opnsense_dashboard_widget_sequence[].column  |    `string`    | The number of the column to show the widget in, in `colX` format, where `X` is the column number. |


Dependencies
------------

N/A.

Example Playbook
----------------

```yaml
- name: Configure the dashboard on all firewalls
  hosts: opnsense

  roles:
    - role: mirceanton.opnsense_dashboard
      vars:
        opnsense_dashboard_columns: 3
        opnsense_dashboard_traphic_graph: wan,lan
        opnsense_dashboard_widget_sequence:
            - widget: system_information-container
              position: '00000000'
              column: col1
            - widget: traffic_graphs-container
              position: '00000001'
              column: col4
            - widget: services_status-container
              position: '00000002'
              column: col5
            - widget: interface_list-container
              position: '00000003'
              column: col5
            - widget: gateways-container
              position: '00000004'
              column: col5
```

License
-------

MIT

Author Information
------------------

A role developed by [Mircea-Pavel ANTON](https://www.mirceanton.com).
