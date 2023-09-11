# useful-scripts

## Obtener pares de claves o key-pairs ssh en uso en ec2

``` aws ec2 --profile=YOUR_PROFILE describe-key-pairs --query 'KeyPairs[].[KeyName]' --output text | xargs -I {} aws ec2 --profile=YOUR_PROFILE describe-instances --filters 'Name=key-name,Values={}' --query 'Reservations[].Instances[].[KeyName]' --output text | uniq ```
