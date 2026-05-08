import requests
import json 

def emotion_detector(text_to_analyse): 
    url = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict' 
    myobj = { "raw_document": { "text": text_to_analyse } } 
    header = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"} 
    response = requests.post(url, json = myobj, headers=header)
    formatted_response = json.loads(response.text)
    emotionPredictions = formatted_response['emotionPredictions']
    emotion = emotionPredictions[0]['emotion']
    anger_score = emotion['anger']
    disgust_score = emotion['disgust']
    fear_score = emotion['fear']
    joy_score = emotion['joy']
    sadness_score = emotion['sadness']

    maxEmotion ='anger'
    maxValue = anger_score

    if maxValue < disgust_score:
        maxValue = disgust_score
        maxEmotion = 'disgust'

    if maxValue < fear_score:
        maxValue = fear_score
        maxEmotion = 'fear'

    if maxValue < joy_score:
        maxValue = joy_score
        maxEmotion = 'joy'

    if maxValue < sadness_score:
        maxValue = sadness_score
        maxEmotion = 'sadness' 

    response = {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score,
        'dominant_emotion': maxEmotion
    }
    
    return response
