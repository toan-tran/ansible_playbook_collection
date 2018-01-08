# Wait for hosts to be ready

## Introduction

This simple role force localhost to wait for remote hosts to be ready. It is usedful if remote hosts
are just created; e.g. Cloud VMs .

## Variables:

 - wait_host_sleep: (optional) Time beetween check. Default: 10 seconds
 - wait_host_timeout: (optional) Timeout for checking. Default: 120 seconds

## Notes

This role MUST be called with gather_facts off, since the remote hosts maybe not be ready!
