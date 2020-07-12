.PHONY: all clean
.DEFAULT_GOAL := help
all: deploy

help:
	@echo "run 'make deploy' to deploy all resource"
	@echo "run 'make cleanup' to clean up all resources"

deploy:
	@echo "Deploy all resources"
	@kubectl apply -f *.yaml

cleanup:
	@echo "Clean up all resources"
	@kubectl delete -f *.yaml