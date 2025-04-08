UTS I Made Ananta Putra ( 2201020051 ) 

import React, { useState } from 'react';
import { View, Text, TextInput, Button, ScrollView, StyleSheet } from 'react-native';
import { RadioButton } from 'react-native-paper';

const HealthSurvey = () => {
  const [name, setName] = useState('');
  const [age, setAge] = useState('');
  const [selectedSymptom, setSelectedSymptom] = useState('');
  const [submitted, setSubmitted] = useState(false);

  const handleSubmit = () => {
    if (!name || !age || !selectedSymptom) {
      alert('Harap isi semua bidang');
      return;
    }
    setSubmitted(true);
  };

  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.title}>Survei Kesehatan</Text>

      <Text style={styles.label}>Nama:</Text>
      <TextInput
        style={styles.input}
        placeholder="Masukkan nama"
        value={name}
        onChangeText={setName}
      />

      <Text style={styles.label}>Usia:</Text>
      <TextInput
        style={styles.input}
        placeholder="Masukkan usia"
        keyboardType="numeric"
        value={age}
        onChangeText={setAge}
      />

      <Text style={styles.label}>Pilih Gejala yang dialami:</Text>
      <RadioButton.Group
        onValueChange={value => setSelectedSymptom(value)}
        value={selectedSymptom}
      >
        <View style={styles.radioRow}>
          <RadioButton value="Demam" />
          <Text>Demam</Text>
        </View>
        <View style={styles.radioRow}>
          <RadioButton value="Batuk" />
          <Text>Batuk</Text>
        </View>
        <View style={styles.radioRow}>
          <RadioButton value="Sesak Nafas" />
          <Text>Sesak Nafas</Text>
        </View>
      </RadioButton.Group>

      <View style={styles.buttonContainer}>
        <Button title="Kirim" onPress={handleSubmit} color="#4CAF50" />
      </View>

      {submitted && (
        <View style={styles.resultContainer}>
          <Text style={styles.resultTitle}>Hasil Survei</Text>
          <Text style={styles.resultText}>Nama: {name}</Text>
          <Text style={styles.resultText}>Usia: {age}</Text>
          <Text style={styles.resultText}>Gejala: {selectedSymptom}</Text>
        </View>
      )}
    </ScrollView>
  );
};

const styles = StyleSheet.create({
  container: {
    padding: 20,
    backgroundColor: '#F9F9F9',
    flexGrow: 1
  },
  title: {
    fontSize: 26,
    fontWeight: 'bold',
    marginBottom: 20,
    textAlign: 'center',
    color: '#333'
  },
  label: {
    fontSize: 16,
    marginBottom: 5,
    color: '#555'
  },
  input: {
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 8,
    padding: 10,
    marginBottom: 15,
    backgroundColor: '#fff'
  },
  radioRow: {
    flexDirection: 'row',
    alignItems: 'center',
    marginBottom: 10
  },
  buttonContainer: {
    marginTop: 20,
    marginBottom: 20
  },
  resultContainer: {
    padding: 15,
    backgroundColor: '#E8F5E9',
    borderRadius: 10
  },
  resultTitle: {
    fontSize: 20,
    fontWeight: 'bold',
    marginBottom: 10,
    color: '#2E7D32'
  },
  resultText: {
    fontSize: 16,
    marginBottom: 5
  }
});

export default HealthSurvey;
