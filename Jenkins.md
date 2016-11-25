## Disable all Nodes
run in "nodes" jenkins path
```
tmp=$(mktemp)
cat > $tmp <<EOF
  <temporaryOfflineCause class="hudson.slaves.OfflineCause$UserCause">
    <timestamp>1502904599005</timestamp>
    <description>
      <holder>
        <owner>hudson.slaves.Messages</owner>
      </holder>
      <key>SlaveComputer.DisconnectedBy</key>
      <args>
        <string>anonymous</string>
        <string> : Maintenance</string>
      </args>
    </description>
  </temporaryOfflineCause>
EOF

sed "/<slave/r $tmp" */config.xml
```
