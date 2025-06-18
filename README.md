# Lockset

## Original repo

`github.com/optimus-hft/lockset`

## GoLang Dynamic Mutexes
Lockset provides dynamic mutexes based on lock keys. Each key is locked and unlocked separately and does not affect other keys.
Instead of protecting everything with a giant mutex, Different parts of code can be protected by a tiny mutex in isolation to provide more throughput and concurrency.

## Getting Started
### Installation
```
go get github.com/ogiusek/lockset
```

### Usage

```go
package cmd

import lockset "github.com/ogiusek/lockset"

func main() {
	s := lockset.New()

	s.Lock("lock1")
	defer s.Unlock("lock1")

	locked := s.TryLock("lock2")
	if locked {
		defer s.Unlock("lock2")
	}
}
```

## Contributing
Pull requests and bug reports are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
This project is licensed under the MIT License.
