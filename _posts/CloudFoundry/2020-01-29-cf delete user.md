---
layout: post
title: cf org에 등록되어 있는 user를 삭제
category: CloudFoundry
tags:
  - cloudfoundry
  - cf curl -X DELETE '/v2/organizations/<ORG_GUID>/users'
  - cf org에 등록되어 있는 user를 삭제하고 싶을때
---





사용자 생성시 cf 쪽에 정확히 등록되는지 확인 테스트 중

DB에도 없는 사용자가 등록이 되어있어서 cf 쪽 명령어를 통해 자체 삭제할 필요가 있었다.



- 기존

```
ubuntu@inception:~$ cf curl /v2/organizations/575cf8b3-a59a-4ab5-806d-9494d60b1425/users
{
   "total_results": 3,
   "total_pages": 1,
   "prev_url": null,
   "next_url": null,
   "resources": [
      {
         "metadata": {
            "guid": "9ec39bd6-56e5-4beb-81e9-798d2d0eddd3",
            "url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3",
            "created_at": "2019-01-16T02:13:47Z",
            "updated_at": "2019-01-16T02:13:47Z"
         },
         "entity": {
            "admin": false,
            "active": false,
            "default_space_guid": null,
            "username": "abcde",
            "spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/spaces",
            "organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/organizations",
            "managed_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/managed_organizations",
            "billing_managed_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/billing_managed_organizations",
            "audited_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/audited_organizations",
            "managed_spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/managed_spaces",
            "audited_spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/audited_spaces"
         }
      },
      {
         "metadata": {
            "guid": "c72d8d75-4df4-4555-a514-bbd675ce9039",
            "url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039",
            "created_at": "2020-01-23T00:54:30Z",
            "updated_at": "2020-01-23T00:54:30Z"
         },
         "entity": {
            "admin": false,
            "active": false,
            "default_space_guid": null,
            "username": "swookwon2",
            "spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/spaces",
            "organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/organizations",
            "managed_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/managed_organizations",
            "billing_managed_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/billing_managed_organizations",
            "audited_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/audited_organizations",
            "managed_spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/managed_spaces",
            "audited_spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/audited_spaces"
         }
      },
      {
         "metadata": {
            "guid": "0c2f6361-fd87-4454-8343-b59e2359d189",
            "url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189",
            "created_at": "2020-01-28T05:50:06Z",
            "updated_at": "2020-01-28T05:50:06Z"
         },
         "entity": {
            "admin": false,
            "active": false,
            "default_space_guid": null,
            "username": "swookwon4",
            "spaces_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/spaces",
            "organizations_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/organizations",
            "managed_organizations_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/managed_organizations",
            "billing_managed_organizations_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/billing_managed_organizations",
            "audited_organizations_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/audited_organizations",
            "managed_spaces_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/managed_spaces",
            "audited_spaces_url": "/v2/users/0c2f6361-fd87-4454-8343-b59e2359d189/audited_spaces"
         }
      }
   ]
}
```



- 유저목록중 `swookwon4` 를 삭제하고 싶어서 아래 명령어 입력
- `cf curl -X DELETE 'v2/organizations/해당 org의 guid/users' -d '{"username" : "swookwon4"}'`

- 결과

```
ubuntu@inception:~$ cf curl /v2/organizations/575cf8b3-a59a-4ab5-806d-9494d60b1425/users
{
   "total_results": 3,
   "total_pages": 1,
   "prev_url": null,
   "next_url": null,
   "resources": [
      {
         "metadata": {
            "guid": "9ec39bd6-56e5-4beb-81e9-798d2d0eddd3",
            "url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3",
            "created_at": "2019-01-16T02:13:47Z",
            "updated_at": "2019-01-16T02:13:47Z"
         },
         "entity": {
            "admin": false,
            "active": false,
            "default_space_guid": null,
            "username": "abcde",
            "spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/spaces",
            "organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/organizations",
            "managed_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/managed_organizations",
            "billing_managed_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/billing_managed_organizations",
            "audited_organizations_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/audited_organizations",
            "managed_spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/managed_spaces",
            "audited_spaces_url": "/v2/users/9ec39bd6-56e5-4beb-81e9-798d2d0eddd3/audited_spaces"
         }
      },
      {
         "metadata": {
            "guid": "c72d8d75-4df4-4555-a514-bbd675ce9039",
            "url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039",
            "created_at": "2020-01-23T00:54:30Z",
            "updated_at": "2020-01-23T00:54:30Z"
         },
         "entity": {
            "admin": false,
            "active": false,
            "default_space_guid": null,
            "username": "swookwon2",
            "spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/spaces",
            "organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/organizations",
            "managed_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/managed_organizations",
            "billing_managed_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/billing_managed_organizations",
            "audited_organizations_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/audited_organizations",
            "managed_spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/managed_spaces",
            "audited_spaces_url": "/v2/users/c72d8d75-4df4-4555-a514-bbd675ce9039/audited_spaces"
         }
      }
   ]
}
```







---

### Reference

[Create command org-remove-user #781](https://github.com/cloudfoundry/cli/issues/781)

