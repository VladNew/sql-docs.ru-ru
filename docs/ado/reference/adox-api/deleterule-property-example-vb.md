---
title: Пример свойства DeleteRule (Visual Basic) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- DeleteRule property [ADOX], Visual Basic example
ms.assetid: 9ba00118-a80d-4a6d-a7d6-4f5492fb7ded
author: rothja
ms.author: jroth
ms.openlocfilehash: 928da8cdfa8bb693bde69781ce40ecad7343c038
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763925"
---
# <a name="deleterule-property-example-vb"></a>Пример свойства DeleteRule (Visual Basic)
В этом примере демонстрируется свойство [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) объекта [Key](../../../ado/reference/adox-api/key-object-adox.md) . Код добавляет новую [таблицу](../../../ado/reference/adox-api/table-object-adox.md) , а затем определяет новый первичный ключ, устанавливая для **DeleteRule** значение **адрикаскаде**.  
  
```  
' BeginDeleteRuleVB  
Sub Main()  
    On Error GoTo DeleteRuleXError  
  
    Dim kyPrimary As New ADOX.Key  
    Dim cat As New ADOX.Catalog  
    Dim tblNew As New ADOX.Table  
  
    ' Connect the catalog  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
                     "data source='Northwind.mdb';"  
  
    ' Name new table  
    tblNew.Name = "NewTable"  
  
    ' Append a numeric and a text field to new table.  
    tblNew.Columns.Append "NumField", adInteger, 20  
    tblNew.Columns.Append "TextField", adVarWChar, 20  
  
    ' Append the new table  
    cat.Tables.Append tblNew  
  
    ' Define the Primary key  
    kyPrimary.Name = "NumField"  
    kyPrimary.Type = adKeyPrimary  
    kyPrimary.RelatedTable = "Customers"  
    kyPrimary.Columns.Append "NumField"  
    kyPrimary.Columns("NumField").RelatedColumn = "CustomerId"  
    kyPrimary.DeleteRule = adRICascade  
  
    ' Append the primary key  
    cat.Tables("NewTable").Keys.Append kyPrimary  
    Debug.Print "The primary key is appended."  
  
    'Delete the table as this is a demonstration.  
    cat.Tables.Delete tblNew.Name  
    Debug.Print "The primary key is deleted."  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set kyPrimary = Nothing  
    Set tblNew = Nothing  
    Exit Sub  
  
DeleteRuleXError:  
  
    Set cat = Nothing  
    Set kyPrimary = Nothing  
    Set tblNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndDeleteRuleVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство DeleteRule (ADOX)](../../../ado/reference/adox-api/deleterule-property-adox.md)   
 [Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)
