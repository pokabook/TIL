# Service Account (SA)

### Service Account

- 사람이 아닌 machine이 사용하는 account
- 사용자 어카운트는 **kubernetes** 관리 대상이 아님
- **Pod** 내 프로세스에 identity를 제공
- 모든 **ns**는 default **SA**가 있으며 기본 **kubernetes api**를 사용할 수 있는 제한된 권한을 제공