---
title: "パーティション表現 (テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: b606cd63-755c-4ac0-b19b-95b5363afbdf
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a3df4bd31c72c38a34167693c542b0fce87d8eb4
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="tables---partition-representation"></a>テーブルなパーティション表現
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
運用上の目的のために、結合させるとテーブルを形成する異なる行のサブセットにテーブルを分割することができます。それぞれのサブセットがテーブルのパーティションです。  
  
## <a name="partition-representation"></a>パーティション表現  
 AMO オブジェクトの場合、パーティション表現は <xref:Microsoft.AnalysisServices.Partition> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。  
  
### <a name="partition-in-amo"></a>AMO におけるパーティション  
 AMO を使用してパーティションを管理する場合、テーブル モデル テーブルを表すメジャー グループを探して、そこから作業する必要があります。  
  
 次のコード スニペットでは、パーティションを既存のテーブル モデル テーブルに渡す方法を示します。  
  
```  
  
private void AddPartition(  
                     AMO.Cube modelCube  
                  ,  AMO.DataSource newDatasource  
                  ,  string mgName  
                  ,  string newPartitionName  
                  , string partitionSelectStatement  
                  , Boolean processPartition  
             )  
{  
    mgName = mgName.Trim();  
    newPartitionName = newPartitionName.Trim();  
    partitionSelectStatement = partitionSelectStatement.Trim();  
    //Validate Input  
    if (string.IsNullOrEmpty(newPartitionName) || string.IsNullOrWhiteSpace(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (modelCube.MeasureGroups[mgName].Partitions.ContainsName(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name already defined. Duplicated names are not allowed"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (string.IsNullOrEmpty(partitionSelectStatement) || string.IsNullOrWhiteSpace(partitionSelectStatement))  
    {  
        MessageBox.Show(String.Format("Select statement cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    //Input validated  
    string partitionID = newPartitionName; //Using partition name as the ID  
    AMO.Partition currentPartition = new AMO.Partition(partitionID, partitionID);  
    currentPartition.StorageMode = AMO.StorageMode.InMemory;  
    currentPartition.ProcessingMode = AMO.ProcessingMode.Regular;  
    currentPartition.Source = new AMO.QueryBinding(newDatasource.ID, partitionSelectStatement);  
    modelCube.MeasureGroups[mgName].Partitions.Add(currentPartition);  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        if (processPartition)  
        {  
            modelCube.MeasureGroups[mgName].Partitions[partitionID].Process(AMO.ProcessType.ProcessFull);  
            MessageBox.Show(String.Format("Partition successfully processed."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        }  
  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
## <a name="amo2tabular-sample"></a>AMO2Tabular サンプル  
 ただし、AMO を使用して作成し、パーティションを操作する方法を理解するに表現する際に、AMO to Tabular サンプルのソース コード参照してください。 このサンプルは、Codeplex から入手できます。 このコードに関する重要な注意事項: このコードは、ここで説明する論理的概念を補足するためにのみ提供されています。運用環境では使用しないでください。教育目的以外の目的にも使用しないでください。  
  
  
