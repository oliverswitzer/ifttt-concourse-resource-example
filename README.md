# If This Then That (IFTTT) Concourse Resource Example

---

### You will need to add:

- An untracked file `secrets.yml` containing:

```.yml
ifttt_api_key: <YOUR API KEY>
```

- The IFTTT events that you would like to fire on success or failure of a build to `pipeline.yml`:

```.yml
jobs:
- name: test-app
  plan:
    ...
    on_success:
      put: ifttt
      params:
        event_name: "<YOUR PASSING BUILD EVENT NAME HERE>"
    on_failure:
      put: ifttt
      params:
        event_name: "<YOUR FAILING BUILD EVENT NAME HERE>"

```