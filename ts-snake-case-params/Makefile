TAG_NAME=openapi-generator-sandbox/ts-snake-case-params
DOCKER_COMMAND=@docker run --rm -v $(PWD):/local -t ${TAG_NAME}

.PHONY: default
default: build

.PHONY: build
build: ## build docker image
	@echo 'Starting $@'
	docker build -t ${TAG_NAME} .
	@echo 'Finished $@'

.PHONY: generate
generate: ## Generate API Client
	@echo 'Starting $@'
	${DOCKER_COMMAND} generate -g typescript-fetch \
		-pnpmName='${TAG_NAME}' \
		-psupportsES6=true \
		-ptypescriptThreePlus=true \
		-i /local/spec.yml \
		-o /local/dist
	@echo 'Finished $@'

.PHONY: help
	help: ## Print this help
	@echo 'Usage: make [target]'
	@echo ''
	@echo 'Targets:'
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

