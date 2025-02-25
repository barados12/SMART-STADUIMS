from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

# استبدل بالمفتاح ونقطة النهاية الخاصين بك
key = "your-key-here"
endpoint = "your-endpoint-here"

# إنشاء العميل
credential = AzureKeyCredential(key)
client = TextAnalyticsClient(endpoint=endpoint, credential=credential)

# تحليل المشاعر
documents = ["أحب هذا الحدث الرائع!", "لم أستمتع بالعرض."]
response = client.analyze_sentiment(documents)

for doc in response:
    print(f"النص: {documents[doc.id]}")
    print(f"المشاعر: {doc.sentiment}")
    print(f"النتائج: Positive={doc.confidence_scores.positive:.2f}, Neutral={doc.confidence_scores.neutral:.2f}, Negative={doc.confidence_scores.negative:.2f}")
    print("------")
