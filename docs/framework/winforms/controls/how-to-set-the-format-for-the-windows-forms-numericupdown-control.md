---
title: "Comment&#160;: d&#233;finir le format du contr&#244;le NumericUpDown Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "NumericUpDown (contrôle Windows Forms), mettre en forme les valeurs"
  - "contrôles up-down, mettre en forme les valeurs numériques"
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir le format du contr&#244;le NumericUpDown Windows Forms
Vous pouvez configurer l'affichage des valeurs dans le contrôle <xref:System.Windows.Forms.NumericUpDown> Windows Forms.  La propriété <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> détermine le nombre de chiffres devant apparaître après la virgule décimale ; la valeur par défaut est 0.  La propriété <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> détermine si un séparateur doit être inséré tous les trois chiffres décimaux ; la valeur par défaut est `false`.  Si la propriété <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> a la valeur `true`, le contrôle affiche les valeurs au format hexadécimal à la place du format décimal ; la valeur par défaut est `false`.  
  
### Pour définir le format de la valeur numérique  
  
-   Affichez une valeur décimale en affectant à la propriété <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> un entier et à la propriété <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> la valeur `true` ou `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     ou  
  
-   Affichez une valeur hexadécimale en affectant à la propriété <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> la valeur `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  Même si la valeur est affichée dans le formulaire au format hexadécimal, tous les tests que vous effectuerez sur la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> porteront sur sa valeur décimale.  
  
## Voir aussi  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown, contrôle](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [Vue d'ensemble du contrôle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)