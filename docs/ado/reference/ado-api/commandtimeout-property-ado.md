---
title: "CommandTimeout, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a7848d7fb51a01c35f8a8699b89ea132da36396b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout, propriété (ADO)
Indique le délai d’attente lors de l’exécution d’une commande avant d’abandonner la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique, en secondes, le délai d’attente d’une commande à exécuter. Valeur par défaut est 30.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CommandTimeout** propriété sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet ou [commande](../../../ado/reference/ado-api/command-object-ado.md) objet pour permettre l’annulation d’une [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (méthode) appel, en raison des délais réseau du trafic ou nombre élevé de l’utilisation de serveur. Si l’intervalle défini dans le **CommandTimeout** propriété s’écoule avant que la commande termine l’exécution, une erreur se produit et ADO annule la commande. Si vous définissez la propriété sur zéro, ADO attend indéfiniment que l’exécution est terminée. Assurez-vous que le fournisseur et source de données à laquelle vous écrivez le code prennent en charge la **CommandTimeout** fonctionnalité.  
  
 Le **CommandTimeout** définition sur une **connexion** objet n’a aucun effet le **CommandTimeout** définition sur un **commande** de l’objet sur le même **connexion**, c'est-à-dire le **commande** l’objet **CommandTimeout** propriété n’hérite pas de la valeur de la **deconnexion** l’objet **CommandTimeout** valeur.  
  
 Sur un **connexion** objet, le **CommandTimeout** propriété reste en lecture-écriture après le **connexion** est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout, propriété (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
