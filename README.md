# toy-scheduler-extender
?**predicates.go**?**podFitsOnNode()**???????????????pod????????????????????%2?0??????????????????“???”??????????????


**predicates.go**

```
package controller

import (
...
	"time"
...
)
...
func LuckyPredicate(pod *v1.Pod, node v1.Node) (bool, []string, error) {
	time_get := time.Now().UTC().UnixNano() 
	lucky := (time_get % 2) == 0
	if lucky {
		log.Printf("pod %v/%v is lucky to fit on node %v. Time %v\n", pod.Name, pod.Namespace, node.Name,time_get)
		return true, nil, nil
	}
	log.Printf("pod %v/%v is unlucky to fit on node %v. Time %v\n", pod.Name, 
  ...
}

```


## Notes

- Because `k8s.io/kubernetes` pkg is not intended to be used with go get,so we need use go modules replace to depend these modules, so you must replace `go.mod` to your local k8s path .

- go version 1.14.4, **go.mod** was modified to fit