.. _community.aws.elb_classic_lb_info_module:


*********************************
community.aws.elb_classic_lb_info
*********************************

**Gather information about EC2 Elastic Load Balancers in AWS**


Version added: 1.0.0

.. contents::
   :local:
   :depth: 1


Synopsis
--------
- Gather information about EC2 Elastic Load Balancers in AWS



Requirements
------------
The below requirements are needed on the host that executes this module.

- python >= 3.6
- boto3 >= 1.18.0
- botocore >= 1.21.0


Parameters
----------

.. raw:: html

    <table  border=0 cellpadding=0 class="documentation-table">
        <tr>
            <th colspan="1">Parameter</th>
            <th>Choices/<font color="blue">Defaults</font></th>
            <th width="100%">Comments</th>
        </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>aws_access_key</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div><code>AWS access key</code>. If not set then the value of the <code>AWS_ACCESS_KEY_ID</code>, <code>AWS_ACCESS_KEY</code> or <code>EC2_ACCESS_KEY</code> environment variable is used.</div>
                        <div>The <em>aws_access_key</em> and <em>profile</em> options are mutually exclusive.</div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: ec2_access_key, access_key</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>aws_ca_bundle</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">path</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>The location of a CA Bundle to use when validating SSL certificates.</div>
                        <div>Note: The CA Bundle is read &#x27;module&#x27; side and may need to be explicitly copied from the controller if not run locally.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>aws_config</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">dictionary</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>A dictionary to modify the botocore configuration.</div>
                        <div>Parameters can be found at <a href='https://botocore.amazonaws.com/v1/documentation/api/latest/reference/config.html#botocore.config.Config'>https://botocore.amazonaws.com/v1/documentation/api/latest/reference/config.html#botocore.config.Config</a>.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>aws_secret_key</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div><code>AWS secret key</code>. If not set then the value of the <code>AWS_SECRET_ACCESS_KEY</code>, <code>AWS_SECRET_KEY</code>, or <code>EC2_SECRET_KEY</code> environment variable is used.</div>
                        <div>The <em>aws_secret_key</em> and <em>profile</em> options are mutually exclusive.</div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: ec2_secret_key, secret_key</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>debug_botocore_endpoint_logs</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                    <li>yes</li>
                        </ul>
                </td>
                <td>
                        <div>Use a botocore.endpoint logger to parse the unique (rather than total) &quot;resource:action&quot; API calls made during a task, outputing the set to the resource_actions key in the task results. Use the aws_resource_action callback to output to total list made during a playbook. The ANSIBLE_DEBUG_BOTOCORE_LOGS environment variable may also be used.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>ec2_url</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>URL to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: aws_endpoint_url, endpoint_url</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>names</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">list</span>
                         / <span style="color: purple">elements=string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>List of ELB names to gather information about. Pass this option to gather information about a set of ELBs, otherwise, all ELBs are returned.</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>profile</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>The <em>profile</em> option is mutually exclusive with the <em>aws_access_key</em>, <em>aws_secret_key</em> and <em>security_token</em> options.</div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: aws_profile</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>region</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: aws_region, ec2_region</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>security_token</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">string</span>
                    </div>
                </td>
                <td>
                </td>
                <td>
                        <div><code>AWS STS security token</code>. If not set then the value of the <code>AWS_SECURITY_TOKEN</code> or <code>EC2_SECURITY_TOKEN</code> environment variable is used.</div>
                        <div>The <em>security_token</em> and <em>profile</em> options are mutually exclusive.</div>
                        <div>Aliases <em>aws_session_token</em> and <em>session_token</em> have been added in version 3.2.0.</div>
                        <div style="font-size: small; color: darkgreen"><br/>aliases: aws_session_token, session_token, aws_security_token, access_token</div>
                </td>
            </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="parameter-"></div>
                    <b>validate_certs</b>
                    <a class="ansibleOptionLink" href="#parameter-" title="Permalink to this option"></a>
                    <div style="font-size: small">
                        <span style="color: purple">boolean</span>
                    </div>
                </td>
                <td>
                        <ul style="margin: 0; padding: 0"><b>Choices:</b>
                                    <li>no</li>
                                    <li><div style="color: blue"><b>yes</b>&nbsp;&larr;</div></li>
                        </ul>
                </td>
                <td>
                        <div>When set to &quot;no&quot;, SSL certificates will not be validated for communication with the AWS APIs.</div>
                </td>
            </tr>
    </table>
    <br/>


Notes
-----

.. note::
   - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_PROFILE`` or ``AWS_DEFAULT_PROFILE``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``, ``AWS_CA_BUNDLE``
   - When no credentials are explicitly provided the AWS SDK (boto3) that Ansible uses will fall back to its configuration files (typically ``~/.aws/credentials``). See https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html for more information.
   - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be defined in the configuration files.



Examples
--------

.. code-block:: yaml

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    # Output format tries to match amazon.aws.ec2_elb_lb module input parameters

    # Gather information about all ELBs
    - community.aws.elb_classic_lb_info:
      register: elb_info

    - ansible.builtin.debug:
        msg: "{{ item.dns_name }}"
      loop: "{{ elb_info.elbs }}"

    # Gather information about a particular ELB
    - community.aws.elb_classic_lb_info:
        names: frontend-prod-elb
      register: elb_info

    - ansible.builtin.debug:
        msg: "{{ elb_info.elbs.0.dns_name }}"

    # Gather information about a set of ELBs
    - community.aws.elb_classic_lb_info:
        names:
        - frontend-prod-elb
        - backend-prod-elb
      register: elb_info

    - ansible.builtin.debug:
        msg: "{{ item.dns_name }}"
      loop: "{{ elb_info.elbs }}"



Return Values
-------------
Common return values are documented `here <https://docs.ansible.com/ansible/latest/reference_appendices/common_return_values.html#common-return-values>`_, the following are the fields unique to this module:

.. raw:: html

    <table border=0 cellpadding=0 class="documentation-table">
        <tr>
            <th colspan="1">Key</th>
            <th>Returned</th>
            <th width="100%">Description</th>
        </tr>
            <tr>
                <td colspan="1">
                    <div class="ansibleOptionAnchor" id="return-"></div>
                    <b>elbs</b>
                    <a class="ansibleOptionLink" href="#return-" title="Permalink to this return value"></a>
                    <div style="font-size: small">
                      <span style="color: purple">list</span>
                    </div>
                </td>
                <td>always</td>
                <td>
                            <div>a list of load balancers</div>
                    <br/>
                        <div style="font-size: smaller"><b>Sample:</b></div>
                        <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">{&#x27;elbs&#x27;: [{&#x27;attributes&#x27;: {&#x27;access_log&#x27;: {&#x27;enabled&#x27;: False}, &#x27;connection_draining&#x27;: {&#x27;enabled&#x27;: True, &#x27;timeout&#x27;: 300}, &#x27;connection_settings&#x27;: {&#x27;idle_timeout&#x27;: 60}, &#x27;cross_zone_load_balancing&#x27;: {&#x27;enabled&#x27;: True}}, &#x27;availability_zones&#x27;: [&#x27;us-east-1a&#x27;, &#x27;us-east-1b&#x27;, &#x27;us-east-1c&#x27;, &#x27;us-east-1d&#x27;, &#x27;us-east-1e&#x27;], &#x27;backend_server_description&#x27;: [], &#x27;canonical_hosted_zone_name&#x27;: &#x27;test-lb-XXXXXXXXXXXX.us-east-1.elb.amazonaws.com&#x27;, &#x27;canonical_hosted_zone_name_id&#x27;: &#x27;XXXXXXXXXXXXXX&#x27;, &#x27;created_time&#x27;: &#x27;2017-08-23T18:25:03.280000+00:00&#x27;, &#x27;dns_name&#x27;: &#x27;test-lb-XXXXXXXXXXXX.us-east-1.elb.amazonaws.com&#x27;, &#x27;health_check&#x27;: {&#x27;healthy_threshold&#x27;: 10, &#x27;interval&#x27;: 30, &#x27;target&#x27;: &#x27;HTTP:80/index.html&#x27;, &#x27;timeout&#x27;: 5, &#x27;unhealthy_threshold&#x27;: 2}, &#x27;instances&#x27;: [], &#x27;instances_inservice&#x27;: [], &#x27;instances_inservice_count&#x27;: 0, &#x27;instances_outofservice&#x27;: [], &#x27;instances_outofservice_count&#x27;: 0, &#x27;instances_unknownservice&#x27;: [], &#x27;instances_unknownservice_count&#x27;: 0, &#x27;listener_descriptions&#x27;: [{&#x27;listener&#x27;: {&#x27;instance_port&#x27;: 80, &#x27;instance_protocol&#x27;: &#x27;HTTP&#x27;, &#x27;load_balancer_port&#x27;: 80, &#x27;protocol&#x27;: &#x27;HTTP&#x27;}, &#x27;policy_names&#x27;: []}], &#x27;load_balancer_name&#x27;: &#x27;test-lb&#x27;, &#x27;policies&#x27;: {&#x27;app_cookie_stickiness_policies&#x27;: [], &#x27;lb_cookie_stickiness_policies&#x27;: [], &#x27;other_policies&#x27;: []}, &#x27;scheme&#x27;: &#x27;internet-facing&#x27;, &#x27;security_groups&#x27;: [&#x27;sg-29d13055&#x27;], &#x27;source_security_group&#x27;: {&#x27;group_name&#x27;: &#x27;default&#x27;, &#x27;owner_alias&#x27;: &#x27;XXXXXXXXXXXX&#x27;}, &#x27;subnets&#x27;: [&#x27;subnet-XXXXXXXX&#x27;, &#x27;subnet-XXXXXXXX&#x27;], &#x27;tags&#x27;: {}, &#x27;vpc_id&#x27;: &#x27;vpc-c248fda4&#x27;}]}</div>
                </td>
            </tr>
    </table>
    <br/><br/>


Status
------


Authors
~~~~~~~

- Michael Schultz (@mjschultz)
- Fernando Jose Pando (@nand0p)
