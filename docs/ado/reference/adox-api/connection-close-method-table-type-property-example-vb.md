---
title: "Fermeture de la connexion (méthode), exemple de propriété Table Type (VB) | Documents Microsoft"
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
dev_langs:
- VB
helpviewer_keywords:
- Close method [ADOX], Visual Basic example
- Type property [ADOX], Visual Basic example
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bdc520343baf5e00091aab8d683b6e6ea8456f4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="connection-close-method-table-type-property-example-vb"></a>Méthode de fermeture de connexion, exemple de propriété Table Type (VB)
Définition de la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété **rien** doit fermer la connexion au catalogue. Collections associées seront vides. Tous les objets qui ont été créés à partir des objets de schéma dans le catalogue sont orphelins. Toutes les propriétés sur les objets qui ont été mis en cache seront toujours disponibles, mais toute tentative de lecture des propriétés qui requiert un appel au fournisseur échoue.  
  
```  
' BeginCloseConnectionVB  
Sub Main()  
    On Error GoTo CloseConnectionByNothingError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Set tbl = cat.Tables(0)  
    Debug.Print tbl.Type    ' Cache tbl.Type info  
    Set cat.ActiveConnection = Nothing  
    Debug.Print tbl.Type    ' tbl is orphaned  
    ' Previous line will succeed if this info was cached.  
    Debug.Print tbl.Columns(0).DefinedSize  
    ' Previous line will fail if this info has not been cached.  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CloseConnectionByNothingError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCloseConnectionVB  
```  
  
 Fermer un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet qui a été utilisée pour ouvrir le catalogue doit avoir le même effet que définir le **ActiveConnection** propriété **rien**.  
  
```  
Attribute VB_Name = "Connection"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Objet table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Collection de tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type, propriété (table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
