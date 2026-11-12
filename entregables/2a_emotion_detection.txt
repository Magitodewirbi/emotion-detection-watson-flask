"""Detect emotions using Watson NLP."""
import json
import requests


def emotion_detector(text_to_analyze):
    """Return emotion scores and the dominant emotion, or None for HTTP 400."""
    response = requests.post(
        "https://sn-watson-emotion.labs.skills.network/v1/"
        "watson.runtime.nlp.v1/NlpService/EmotionPredict",
        headers={"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"},
        json={"raw_document": {"text": text_to_analyze}}, timeout=30,
    )
    return response.text
