---
title: "Comment&#160;: importer des assertions de strat&#233;gie personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: importer des assertions de strat&#233;gie personnalis&#233;es
Les assertions de stratégie décrivent les fonctions et les exigences d’un point de terminaison de service.  Les applications clientes peuvent utiliser des assertions de stratégie dans les métadonnées de service pour configurer la liaison cliente ou personnaliser le contrat de service d’un point de terminaison de service.  
  
 Assertions de stratégie personnalisées sont importées en implémentant le <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> interface et en passant cet objet, le système de métadonnées ou en enregistrant l’implémentation de type dans votre fichier de configuration d’application.  Les implémentations de la <xref:System.ServiceModel.Description.IPolicyImportExtension> interface doit fournir un constructeur par défaut.  
  
### <a name="to-import-custom-policy-assertions"></a>Pour importer des assertions de stratégie personnalisées  
  
1.  Implémentez la <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> interface sur une classe. Reportez-vous aux procédures ci-dessous.  
  
2.  Insérez l'importateur de stratégie personnalisé selon l'une des méthodes suivantes :  
  
3.  Utilisation d'un fichier de configuration. Reportez-vous aux procédures ci-dessous.  
  
4.  À l’aide d’un fichier de configuration avec [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Reportez-vous aux procédures ci-dessous.  
  
5.  Insertion par programme de l'importateur de stratégie. Reportez-vous aux procédures ci-dessous.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Pour implémenter l'interface System.ServiceModel.Description.IPolicyImportExtension sur une classe  
  
1.  Dans le <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName> (méthode), pour chaque objet de stratégie qui vous intéressez, rechercher les assertions de stratégie que vous souhaitez importer en appelant la méthode appropriée (en fonction de l’étendue de l’assertion que vous le souhaitez) sur le <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=fullName> objet passé à la méthode. L’exemple de code suivant montre comment utiliser le <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName> méthode pour localiser l’assertion de stratégie personnalisée et le supprime de la collection en une seule étape. Si vous utilisez la méthode de suppression pour localiser et supprimer l'assertion, l'étape 4 n'est pas nécessaire.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  Traitez les assertions de stratégie. Notez que le système de stratégie ne normalise pas les stratégies imbriquées et `wsp:optional`. Vous devez traiter ces constructions dans votre implémentation d'extension d'importation de stratégie.  
  
3.  Exécutez la personnalisation sur la liaison ou le contrat qui prend en charge la fonction ou la spécification spécifiée par l'assertion de stratégie. En général, les assertions indiquent qu’une liaison requiert une configuration particulière ou un élément de liaison spécifique. Apportez ces modifications en accédant à la <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=fullName> propriété. D'autres assertions requièrent la modification du contrat.  Vous pouvez accéder et modifier le contrat à l’aide de la <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=fullName> propriété.  Notez que votre importateur de stratégie peut être appelé plusieurs fois pour la même liaison et le même contrat, mais pour des alternatives de stratégie différentes en cas d’échec de l’importation d’une alternative de stratégie. Votre code doit être résilient à ce comportement.  
  
4.  Supprimez l'assertion de stratégie personnalisée de la collection d'assertions. Si vous ne supprimez pas l'assertion, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suppose que l'importation de stratégie a échoué et n'importe pas la liaison associée. Si vous avez utilisé le <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName> méthode pour localiser l’assertion de stratégie personnalisée et le supprime de la collection en une seule étape, vous n’avez pas à effectuer cette étape.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Pour insérer l'importateur de stratégie personnalisé dans le système de métadonnées à l'aide d'un fichier de configuration  
  
1.  Ajouter le type d’importateur à la `<extensions>` élément à l’intérieur du [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) élément dans le fichier de configuration du client.  
  
     [!code[CustomPolicySample#7](../../../../samples/snippets/common/VS_Snippets_CFX/custompolicysample/common/client.exe.config#7)]
     [!code-csharp[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
     [!code-vb[CustomPolicySample#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.exe.config#7)]  
  
2.  Dans l’application cliente, utilisez la <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName> ou <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> pour résoudre les métadonnées et l’importateur étant appelé automatiquement.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Pour insérer l'importateur de stratégie personnalisé dans le système de métadonnées à l'aide de Svcutil.exe  
  
1.  Ajouter le type d’importateur à la `<extensions>` élément à l’intérieur du [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) élément dans le fichier de configuration Svcutil.exe.config. Vous pouvez également pointer Svcutil.exe pour charger les types d'importateur de stratégie enregistrés dans un autre fichier de configuration à l'aide de l'option `/svcutilConfig`.  
  
2.  Utilisez [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour importer les métadonnées, l’importateur est appelée automatiquement.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Pour insérer par programme l'importateur de stratégie personnalisé dans le système de métadonnées  
  
1.  Ajoutez l’importateur à la <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=fullName> propriété (par exemple, si vous utilisez la <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>) avant d’importer les métadonnées.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 [Extension du système de métadonnées](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)