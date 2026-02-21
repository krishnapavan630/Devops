# JQ Quick Revision Guide (DevOps Friendly)

## 1. What is jq?

`jq` is a lightweight command-line JSON processor used to parse, filter,
and transform JSON data in Linux.

------------------------------------------------------------------------

## 2. Installation

### RHEL / CentOS / Amazon Linux

``` bash
sudo yum install jq
```

### Ubuntu / Debian

``` bash
sudo apt install jq
```

------------------------------------------------------------------------

## 3. Basic Syntax

``` bash
jq 'filter' file.json
```

Use `-r` for raw output (removes quotes):

``` bash
jq -r '.name' file.json
```

------------------------------------------------------------------------

## 4. Extract Values

### Sample JSON

``` json
{
  "name": "Krishna",
  "age": 28,
  "skills": ["Linux", "AWS", "Shell"]
}
```

### Get a Field

``` bash
jq -r '.name' file.json
```

### Get Array Elements

``` bash
jq -r '.skills[]' file.json
```

------------------------------------------------------------------------

## 5. Loop Through JSON Array (Shell Script)

``` bash
jq -c '.users[]' data.json | while read user
do
  name=$(echo "$user" | jq -r '.name')
  role=$(echo "$user" | jq -r '.role')
  echo "User: $name | Role: $role"
done
```

`-c` prints compact JSON (one object per line).

------------------------------------------------------------------------

## 6. AWS CLI + jq (Very Common)

``` bash
aws ec2 describe-instances --region ap-south-1 | jq -r '.Reservations[].Instances[].InstanceId'
```

Loop example:

``` bash
instance_ids=$(aws ec2 describe-instances | jq -r '.Reservations[].Instances[].InstanceId')

for id in $instance_ids
do
  echo "Instance ID: $id"
done
```

------------------------------------------------------------------------

## 7. Filtering Data

### Select Condition

``` bash
jq 'select(.age > 25)' file.json
```

### Filter Inside Array

``` bash
jq '.users[] | select(.role=="admin")' file.json
```

------------------------------------------------------------------------

## 8. Passing Shell Variables to jq

``` bash
username="krishna"

jq --arg user "$username" '.name = $user' file.json
```

`--arg` safely passes shell variables.

------------------------------------------------------------------------

## 9. Update JSON File

``` bash
tmp=$(mktemp)
jq '.age = 30' file.json > "$tmp" && mv "$tmp" file.json
```

jq does NOT edit files directly --- always redirect output.

------------------------------------------------------------------------

## 10. Validate JSON

``` bash
jq empty file.json
```

Use in script:

``` bash
if ! jq empty file.json 2>/dev/null; then
  echo "Invalid JSON"
  exit 1
fi
```

------------------------------------------------------------------------

## 11. Best Practices

✔ Always use `-r` in shell scripts\
✔ Avoid useless `cat`\
✔ Use `-c` for looping\
✔ Validate JSON before processing\
✔ Use `--arg` for passing variables

------------------------------------------------------------------------

## 12. Commonly Used Filters (Quick Memory)

  Purpose          Command
  ---------------- ---------------------------------
  Pretty Print     `jq '.' file.json`
  Get Key          `jq -r '.key' file.json`
  Array Items      `jq '.array[]' file.json`
  Nested Key       `jq '.a.b.c' file.json`
  Select           `jq 'select(.id==1)' file.json`
  Compact Output   `jq -c '.users[]' file.json`

------------------------------------------------------------------------

### End of Quick Revision Guide

Keep practicing with AWS CLI, APIs, and shell automation.
