build: ## Build docker image
	docker build -t example01 .

run: ## Run docker image
	docker run example01

help: ## Show this help
	@grep -E '^[.a-zA-Z0-9_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

# Fun command 'for ((i=1; i<=10; i++)); do clear && make run && sleep 30s; done'