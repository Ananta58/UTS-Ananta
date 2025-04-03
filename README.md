# UTS-Ananta

import React, { useState } from 'react';
import { View, Text, TextInput, Button, Alert, ScrollView } from 'react-native';

const HealthSurvey = () => {
  const [name, setName] = useState('');
  const [age, setAge] = useState('');
  const [symptoms, setSymptoms] = useState('');

  const handleSubmit = () => {
    if (!name || !age || !symptoms) {
      Alert.alert('Error', 'Harap isi semua bidang');
      return;
    }
    Alert.alert('Terima Kasih', `Nama: ${name}\nUsia: ${age}\nGejala: ${symptoms}`);
  };

  return (
    <ScrollView style={{ padding: 20 }}>
      <Text style={{ fontSize: 24, fontWeight: 'bold', marginBottom: 20 }}>Survei Kesehatan</Text>
      
      <Text>Nama:</Text>
      <TextInput
        style={{ borderWidth: 1, padding: 10, marginBottom: 10 }}
        placeholder="Masukkan nama"
        value={name}
        onChangeText={setName}
      />
      
      <Text>Usia:</Text>
      <TextInput
        style={{ borderWidth: 1, padding: 10, marginBottom: 10 }}
        placeholder="Masukkan usia"
        keyboardType="numeric"
        value={age}
        onChangeText={setAge}
      />
      
      <Text>Gejala yang dialami:</Text>
      <TextInput
        style={{ borderWidth: 1, padding: 10, marginBottom: 20 }}
        placeholder="Masukkan gejala"
        value={symptoms}
        onChangeText={setSymptoms}
        multiline
      />
      
      <Button title="Kirim" onPress={handleSubmit} />
    </ScrollView>
  );
};

export default HealthSurvey;
