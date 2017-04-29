---
title: "Classe d&#39;&#233;v&#233;nements Broker:Corrupted Message | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Broker:Corrupted Message, classe d'événements"
ms.assetid: 084bf198-2138-438e-bdc7-4ff1e04300f7
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Classe d&#39;&#233;v&#233;nements Broker:Corrupted Message
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un événement **Broker:Corrupted Message** quand Service Broker reçoit un message endommagé.  
  
## Colonnes de données de la classe d'événements Broker:Corrupted Message  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**BigintData1**|**bigint**|Numéro de séquence de ce message.|52|Non|  
|**BinaryData**|**image**|Corps du message.|2|Oui|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**Erreur**|**int**|ID du message dans **sys.messages** destiné au texte de l’événement.|31|Non|  
|**EventClass**|**int**|Type de classe d'événements capturée. Toujours **161** pour **Broker:Corrupted Message**.|27|Non|  
|**EventSequence**|**int**|Numéro de séquence de cet événement.|51|Non|  
|**FileName**|**nvarchar**|Adresse réseau du point de terminaison distant.|36|Non|  
|**GUID**|**uniqueidentifier**|ID de la conversation à laquelle le message endommagé appartient. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|Non|  
|**Host Name**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|**int**|Numéro de fragment de ce message.|25|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectName**|**nvarchar**|Nom de service de l'autre partie de la conversation et chaîne de connexion que la base de données distante a utilisée pour se connecter à cette base de données.|34|Non|  
|**RoleName**|**nvarchar**|Rôle du point de terminaison qui reçoit ce message. Une des valeurs ci-dessous.<br /><br /> **initiateur** : le point de terminaison récepteur est l’initiateur de la conversation.<br /><br /> **cible** : le point de terminaison récepteur est la cible de la conversation.|38|Non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**Severity**|**int**|Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a supprimé le message en raison d'une erreur, il s'agit de la gravité de l'erreur.|29|Non|  
|**SPID**|**int**|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**État**|**int**|Indique l'emplacement dans le code source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a produit l'événement. Chaque emplacement susceptible de générer cet événement possède un code d'état spécifique. Un spécialiste de l'assistance technique Microsoft peut se servir de ce code d'état afin de déterminer où l'événement s'est produit.|30|Non|  
|**TextData**|**ntext**|Description de l'endommagement détecté.|1|Oui|  
|**ID de transaction**|**bigint**|ID affecté à la transaction par le système.|4|Non|  
  
 La colonne **TextData** de cet événement contient un message qui décrit le problème lié au message.  
  
  