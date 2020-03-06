数据库：mol

1、【新增】店铺主体信息

```sql
CREATE TABLE `mall_store` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`store_name` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '店铺名称',	
`store_logo_url` varchar(256) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '店铺logo图片URL',	
`store_owner_id` bigint(20) NOT NULL  COMMENT 'store_company_id',	
`store_owner_name` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT 'MARINE ONLINE',	
`store_type` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '店铺类型:Brank Store|Port Store',	
`store_status` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '店铺状态:Active|InActive',	
`store_desc` varchar(2000) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '店铺简介',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺表';
```



2、【新增】店铺供应商关联表

```sql
CREATE TABLE `mall_store_supply` (
`id` bigint(20) NOT NULL COMMENT 'ID号',
`store_id` bigint(20) NOT NULL  COMMENT '店铺ID',
`company_id` bigint(20) NOT NULL  COMMENT '供应商公司ID,biz_company:biz_ype = erp_supplier or biz_type = all_supplier',
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',
PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺供应商关联表';
```

3、【新增】店铺·banner

```sql
CREATE TABLE `mall_store_banner` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`mall_store_id` bigint(20) NOT NULL  COMMENT '店铺ID',	
`banner_url` varchar(256) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT 'banner图片RUL',	
`banner_status` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '状态:Active|InActive|Deleted',	
`banner_introduction` varchar(2000) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT 'banner图简介',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci  COMMENT='店铺banner表';	
```

4、【新增】店铺联系人

```sql
CREATE TABLE `mall_store_contact` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`mall_store_id` bigint(20) NOT NULL  COMMENT '店铺ID',	
`contact_person_name` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '联系人名称',	
`contact_email` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '联系人邮箱',	
`contact_number` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '联系人电话',	
`company_dept_name` varchar(32) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '联系人部门，手工输入文本',	
`company_job_title` varchar(32) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '联系人Title',	
`contact_status` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '状态:Active|InActive|Deleted',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺联系人表';

```

5、【新增】店铺经营类目

```sql
CREATE TABLE `mall_store_category` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`mall_store_id` bigint(20) NOT NULL  COMMENT '店铺ID',	
`category_id` bigint(18) NOT NULL COMMENT '分类一级ID',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺类目关联表';
```



6、【新增】店铺License

```sql
CREATE TABLE `mall_store_license` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`mall_store_id` bigint(20) NOT NULL  COMMENT '店铺ID',	
`license_name` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '名称',	
`license_image_url` varchar(256) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '图片URL',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
`license_status` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '状态:Active|InActive|Deleted',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺资质表';	
```



7、【新增】店铺港口

```sql
CREATE TABLE `mall_store_port` (	
`id` bigint(20) NOT NULL COMMENT 'ID号',	
`mall_store_id` bigint(20) NOT NULL  COMMENT '店铺ID',	
`port_id` bigint(20) NOT NULL  COMMENT '港口ID',	
`created_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',	
`updated_dttm` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',	
`status` varchar(12) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '状态:Active|InActive|Deleted',	
PRIMARY KEY (`id`)	
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='店铺港口关联表';
```

8、【新增】地址库

```sql
CREATE TABLE `mall_user_address` (
  `id` bigint(18) NOT NULL,
  `user_id` bigint(18) DEFAULT NULL COMMENT '用户ID',
  `address` varchar(256) NOT NULL COMMENT '物流地址',
  `company_name` varchar(64) NOT NULL COMMENT '公司名称',
  `contact_person` varchar(64) NOT NULL COMMENT '联系人',
  `email` varchar(64) NOT NULL COMMENT 'Email地址',
  `contact_no_country` varchar(64) NOT NULL COMMENT '电话国家代码+86',
  `contact_no` varchar(64) NOT NULL COMMENT '联系电话1351234567',
  `postal_code` varchar(64) NOT NULL COMMENT '邮编',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=COMPACT  COMMENT='用户地址簿表';
```



9、【新增】Timeline

```sql
CREATE TABLE `erp_order_timeline` (
`id` bigint(20) NOT NULL COMMENT 'ID号',
`order_id` bigint(20) NOT NULL COMMENT 'order_id',
`document_name` varchar(128) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '附件名',
`document_url` varchar(128) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT 'URL地址',
`remarks` varchar(1000) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '' COMMENT '备注信息',
`create_by` varchar(32) DEFAULT NULL,
`create_time` timestamp NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间,DB insert会生成',
`update_by` varchar(32) DEFAULT NULL,
`update_time` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '最后更新时间，DB update会生成',
`deleted` tinyint(4) NOT NULL DEFAULT '0' COMMENT '是否已删除，0.没有 1.已删除',
PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='Erp订单物流表' ;
```

