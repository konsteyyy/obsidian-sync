```pseudocode
ADT Keller
	createStack : → Stack
	push : Stack × T → Stack
	top : Stack → T
	pop : Stack → Stack
	isEmpty : Stack → Bool
Axiome:
	K1: isEmpty (createStack) = true
	K2: isEmpty (push(s, x )) = false
	K3: top(push(s, x )) = x
	K4: pop(push(s, x )) = s
```

```haskell
type Stack t=[t]
createStack :: (Stack t)
push :: (Stack t)−>t−>(Stack t)
pop :: (Stack t)−>(Stack t)
top :: (Stack t)−>t
isEmpty :: (Stack t)−>Bool
createStack=[]
push s x = x : s
pop s= tail s
top s= head s
isEmpty []= True
isEmpty _= False
```

### Verifikation der Gesetze


![[Pasted image 20240103123515.png]]

![[Pasted image 20240103123525.png]]