---
title: Sys.xml_schema_model_groups (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_model_groups
- xml_schema_model_groups
- sys.xml_schema_model_groups_TSQL
- xml_schema_model_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_model_groups catalog view
ms.assetid: 566556dc-a8c8-465c-9196-c7e0ae092a8a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04a1fb7af82e1bb8d6cfc09d134e17fc6c61b0c8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysxmlschemamodelgroups-transact-sql"></a>sys.xml_schema_model_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque composant de schéma XML qui est un groupe de modèles, **symbol_space** de **M**...  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**\<héritée de colonnes >**||Hérite des colonnes de [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**compositor**|**char(1)**|Type de compositeur du groupe :<br /><br /> A = XSD \<tous les > groupe<br /><br /> C = XSD \<choix > groupe<br /><br /> S = XSD \<séquence > groupe|  
|**compositor_desc**|**Nvarchar (60)**|Description du type de compositeur du groupe :<br /><br /> XSD_ALL_GROUP<br /><br /> XSD_CHOICE_GROUP<br /><br /> XSD_SEQUENCE_GROUP|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;système de Type XML&#41; affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
