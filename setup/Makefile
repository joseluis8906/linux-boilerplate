.PHONY: foundations
foundations:
	@ansible-playbook ./playbooks/01-foundations.yml -i ./inventory/hosts --user $$USER --ask-pass --ask-become-pass

.PHONY: desktop 
desktop:
	@ansible-playbook ./playbooks/02-bspwm.yml -i ./inventory/hosts --user $$USER --ask-pass --ask-become-pass

.PHONY: dev_env
dev_env:
	@ansible-playbook ./playbooks/03-dev_env.yml -i ./inventory/hosts --user $$USER --ask-pass --ask-become-pass
