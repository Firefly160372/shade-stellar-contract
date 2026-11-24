default: build

all: test

test: build
	cargo test

build:
	stellar contract build
	@ls -l ../../target/wasm32v1-none/release/*.wasm

fixtures:
	stellar contract build
	cp ../../target/wasm32v1-none/release/account.wasm src/tests/fixtures/account.wasm

fixtures-check: fixtures
	@git diff --exit-code src/tests/fixtures/account.wasm || (echo "ERROR: src/tests/fixtures/account.wasm is stale. Run 'make fixtures' and commit the result." && exit 1)
	@echo "OK: src/tests/fixtures/account.wasm is up to date with the account source."

fmt:
	cargo fmt --all

clean:
	cargo clean
