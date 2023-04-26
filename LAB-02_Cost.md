# Cost

## Cloudcustodian

1. Install [cloudcustodian](https://cloudcustodian.io/getting-started):
```
pip3 install c7n
```

2. Install infracost(https://www.infracost.io/docs):
```
brew install infracost
```

3. Clone the reference repo:

```
git clone https://github.com/infracost/example-terraform
```
4. Show cost estimate breakdown:
```
cd my-terraform-project
infracost breakdown --path .
```
