---
title: "Atténuation : MemberDescriptor.Equals | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 409f06f4dfbe7be50dd2c487e49d3d4d8a477539
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-memberdescriptorequals"></a>Atténuation : MemberDescriptor.Equals
En commençant par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], l’implémentation de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>. Étant donné que les méthodes `System.ComponentModel.EventDescriptor.Equals` et `System.ComponentModel.PropertyDescriptor.Equals` héritent de l’implémentation de la classe de base, la modification affecte également ces méthodes.  
  
 Dans les applications qui ciblent des versions du .NET Framework antérieures à [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], une partie du test d’égalité pour la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> comparait incorrectement la propriété <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> d’un objet avec la propriété <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> de l’autre. En commençant par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> compare la propriété <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> des deux objets.  
  
## <a name="impact"></a>Impact  
 Cette modification implémente correctement le test d’égalité pour les objets <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> et doit avoir un impact minimal.  
  
## <a name="mitigation"></a>Atténuation  
 Deux solutions sont disponibles si application cible [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou une version ultérieure de .NET Framework, et dépend du renvoi de `false` par la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> lorsque des descripteurs membres sont équivalents :  
  
-   Vous pouvez refuser cette modification sans modifier votre code source en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :  
  
    ```xml  
  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
  
    ```  
  
-   Vous pouvez modifier votre code source pour restaurer le comportement précédent en comparant manuellement les propriétés <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> et <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> après avoir appelé la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName>, comme dans le fragment de code suivant.  
  
    ```csharp  
  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
  
    ```  
  
    ```  
  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
  
    ```  
  
 Pour les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, vous pouvez activer cette modification en ajoutant la valeur suivante à votre fichier app.config :  
  
```xml  
  
<runtime>  
    \<AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)   
 [Compatibilité des applications dans la version 4.6.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
