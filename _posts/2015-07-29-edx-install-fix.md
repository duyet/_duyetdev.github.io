


Open: **roles/edxapp/tasks/deploy.yml**
Edit line 286: 
````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x .git/.* {{ edxapp_code_dir }}"
````
to 
````
shell: "{{ edxapp_venv_bin }}/python -m compileall -x \".git/*|src/zendesk*\" {{ edxapp_code_dir }}"
````
