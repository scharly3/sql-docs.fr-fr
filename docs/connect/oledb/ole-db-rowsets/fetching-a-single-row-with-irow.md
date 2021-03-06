---
title: Extraction d’une ligne unique avec IRow | Documents Microsoft
description: Extraction d’une ligne unique à l’aide d’interface IRow de pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f34071fd7033c381cfc63fb1bb1937ec718ef19
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="fetching-a-single-row-with-irow"></a>Extraction d'une ligne unique avec IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le **IRow** interface mise en œuvre dans le pilote OLE DB pour SQL Server est simplifiée pour améliorer les performances. **IRow** permet un accès direct aux colonnes d’un objet ligne unique. Si vous savez à l’avance que le résultat d’une exécution de commande génère une ligne exactement, **IRow** extraira les colonnes de cette ligne. Si le jeu de résultats comprend plusieurs lignes, **IRow** exposera uniquement la première ligne.  
  
 Le **IRow** implémentation n’autorise pas aucune navigation de la ligne. Chaque colonne dans la ligne est accédée une seule fois, à une exception près : une colonne peut être accédée une fois pour rechercher la taille de colonne et une autre fois pour extraire les données.  
  
> [!NOTE]  
>  **IRow::Open** prend en charge le seul type DBGUID_STREAM et DBGUID_NULL d’objets à ouvrir.  
  
 Pour obtenir un objet de la ligne à l’aide **ICommand::Execute** méthode, IID_IRow doit être passé. Le **IMultipleResults** interface doit être utilisé pour gérer plusieurs jeux de résultats. **IMultipleResults** prend en charge **IRow** et **IRowset**. **IRowset** est utilisé pour les opérations en bloc.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d’IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
