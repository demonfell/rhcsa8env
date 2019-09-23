# Lab to practice automounting nfs shares with autofs

## Prerequisites
ansible-playbook --tags=begin -u vagrant -i inventory playbooks/autofs_lab.yml

## Background information
- *ipa* is exporting the `/business_shares/indirect` directory as an NFS share, which in turn contains the `north`, `middle`, and `south` subdirectories.
- *ipa* is also exporting the `/business_shares/direct/external` directory as an NFS share.
- The `ops` group consists of the `ops1` and `ops2` users. They have read and
write access to the shared directories `/business_shares/indirect/north`, `/business_ shares/indirect/south`, and `/business_shares/indirect/middle.`
- The `consultants` group consists of the `consultant1` and `consultant2` users. They have read and write access to the `/business_shares/direct/external` shared directory.

Tasks:
- The expected mount points for *system* are `/external` and `/internal.`
- The `/business_shares/direct/external` shared directory should be automounted on *system* using a direct map on `/external`.
- The `/business_shares/indirect/south` shared directory should be automounted on *system* using an indirect map on `/internal/south.`
- The `/businesa_shares/indirect/middle` shared directory should be automounted on *system* using an indirect map on `/internal/middle`.
- The `/business_shares/indirect/north` shared directory should be automounted on *system* using an indirect map on `/internal/north`.
