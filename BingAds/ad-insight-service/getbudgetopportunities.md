---
title: GetBudgetOpportunities Service Operation
ms.service: bing-ads-ad-insight-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Gets the campaign budget opportunities of the specified campaign.
---
# GetBudgetOpportunities Service Operation
Gets the campaign budget opportunities of the specified campaign.

## <a name="request"></a>Request Elements
The *GetBudgetOpportunitiesRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="campaignid"></a>CampaignId|The identifier of the campaign for which you want to discover possible campaign budget opportunities.<br /><br />If this element is nil or empty, then the operation will return all budget opportunities for the account.|**long**|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *GetBudgetOpportunitiesResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="opportunities"></a>Opportunities|An array of [BudgetOpportunity](../ad-insight-service/budgetopportunity.md) data objects that identify the campaigns whose clicks and impressions may increase if you were to apply the suggested budget.<br /><br />The list will not include opportunities for campaigns that are currently paused by the user.<br /><br />Up to 500 opportunities will be returned for the account.|[BudgetOpportunity](budgetopportunity.md) array|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
The following template shows the order of the [body](#request-body) and [header](#request-header) elements for the SOAP request.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetBudgetOpportunities</Action>
    <ApplicationToken i:nil="false">ValueHere</ApplicationToken>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <CustomerAccountId i:nil="false">ValueHere</CustomerAccountId>
    <CustomerId i:nil="false">ValueHere</CustomerId>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
    <Password i:nil="false">ValueHere</Password>
    <UserName i:nil="false">ValueHere</UserName>
  </s:Header>
  <s:Body>
    <GetBudgetOpportunitiesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <CampaignId i:nil="false">ValueHere</CampaignId>
    </GetBudgetOpportunitiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
The following template shows the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <GetBudgetOpportunitiesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Opportunities xmlns:e676="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <e676:BudgetOpportunity>
          <e676:BudgetPoints d4p1:nil="false">
            <e676:BudgetPoint>
              <e676:BudgetAmount>ValueHere</e676:BudgetAmount>
              <e676:BudgetPointType>ValueHere</e676:BudgetPointType>
              <e676:EstimatedWeeklyClicks>ValueHere</e676:EstimatedWeeklyClicks>
              <e676:EstimatedWeeklyCost>ValueHere</e676:EstimatedWeeklyCost>
              <e676:EstimatedWeeklyImpressions>ValueHere</e676:EstimatedWeeklyImpressions>
            </e676:BudgetPoint>
          </e676:BudgetPoints>
          <e676:BudgetType>ValueHere</e676:BudgetType>
          <e676:CampaignId>ValueHere</e676:CampaignId>
          <e676:CurrentBudget>ValueHere</e676:CurrentBudget>
          <e676:IncreaseInClicks>ValueHere</e676:IncreaseInClicks>
          <e676:IncreaseInImpressions>ValueHere</e676:IncreaseInImpressions>
          <e676:PercentageIncreaseInClicks>ValueHere</e676:PercentageIncreaseInClicks>
          <e676:PercentageIncreaseInImpressions>ValueHere</e676:PercentageIncreaseInImpressions>
          <e676:RecommendedBudget>ValueHere</e676:RecommendedBudget>
        </e676:BudgetOpportunity>
      </Opportunities>
    </GetBudgetOpportunitiesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](~/guides/client-libraries.md). See [Bing Ads Code Examples](~/guides/code-examples.md) for more examples.
```csharp
public async Task<GetBudgetOpportunitiesResponse> GetBudgetOpportunitiesAsync(
	long campaignId)
{
	var request = new GetBudgetOpportunitiesRequest
	{
		CampaignId = campaignId
	};

	return (await AdInsightService.CallAsync((s, r) => s.GetBudgetOpportunitiesAsync(r), request));
}
```
```java
static GetBudgetOpportunitiesResponse getBudgetOpportunities(
	java.lang.Long campaignId) throws RemoteException, Exception
{
	GetBudgetOpportunitiesRequest request = new GetBudgetOpportunitiesRequest();

	request.setCampaignId(campaignId);

	return AdInsightService.getService().getBudgetOpportunities(request);
}
```
```php
static function GetBudgetOpportunities(
	$campaignId)

	$getBudgetOpportunitiesRequest = new GetBudgetOpportunitiesRequest();

	$request->CampaignId = $campaignId;

	return $AdInsightProxy->GetService()->GetBudgetOpportunities($request);
}
```
```python
response=adinsight.GetBudgetOpportunities(
	CampaignId=CampaignIdHere
)
```

## Requirements
Service: [AdInsightService.svc v11](https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/v11/AdInsightService.svc)  
Namespace: Microsoft.Advertiser.AdInsight.Api.Service.V11  
