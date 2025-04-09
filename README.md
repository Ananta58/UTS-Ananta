UTS I Made Ananta Putra ( 2201020051 ) 

import React, { useState } from "react";
import { View, Text, FlatList, TextInput, TouchableOpacity, Image } from "react-native";
import { Picker } from "@react-native-picker/picker";

const CoffeePickerView = ({ navigation }) => {
    const [selectedCoffee, setSelectedCoffee] = useState("Espresso");
    const coffeeOptions = ["Espresso", "Latte", "Cappuccino", "Americano", "Mocha"];
    const [searchText, setSearchText] = useState("");
    const [cart, setCart] = useState([]);

    const addToCart = (coffee) => {
        setCart([...cart, coffee]);
    };

    return (
        <View style={{ flex: 1, padding: 20, backgroundColor: "#f5f5f5" }}>
            <TouchableOpacity 
                style={{ backgroundColor: "#D2691E", padding: 15, borderRadius: 10, alignItems: "center", marginBottom: 20 }}
                onPress={() => navigation.navigate('HomeScreen')}
            >
                <Text style={{ color: "white", fontSize: 18 }}>Get Started</Text>
            </TouchableOpacity>

            <View style={{ backgroundColor: "#333", padding: 15, borderRadius: 10 }}>
                <Text style={{ color: "white", fontSize: 14 }}>Location</Text>
                <Text style={{ color: "white", fontSize: 18, fontWeight: "bold" }}>Bilzen, Tanjungbalai</Text>
            </View>
            
            <TextInput 
                style={{ backgroundColor: "white", padding: 10, marginVertical: 10, borderRadius: 10 }}
                placeholder="Search coffee"
                value={searchText}
                onChangeText={setSearchText}
            />
            
            <Picker
                selectedValue={selectedCoffee}
                onValueChange={(itemValue) => setSelectedCoffee(itemValue)}
                style={{ height: 50, width: "100%", backgroundColor: "white", borderRadius: 10 }}
            >
                {coffeeOptions.map((coffee) => (
                    <Picker.Item key={coffee} label={coffee} value={coffee} />
                ))}
            </Picker>

            <View style={{ marginVertical: 20, alignItems: "center" }}>
                <Image source={{ uri: "https://example.com/coffee-image.jpg" }} style={{ width: 200, height: 200, borderRadius: 10 }} />
                <Text style={{ fontSize: 24, fontWeight: "bold", marginVertical: 10 }}>{selectedCoffee}</Text>
                <Text style={{ fontSize: 16, textAlign: "center", paddingHorizontal: 20 }}>
                    A delicious cup of {selectedCoffee} just for you!
                </Text>
            </View>

            <TouchableOpacity 
                style={{ backgroundColor: "brown", padding: 15, borderRadius: 10, alignItems: "center" }}
                onPress={() => addToCart(selectedCoffee)}
            >
                <Text style={{ color: "white", fontSize: 18 }}>Buy Now</Text>
            </TouchableOpacity>

            <Text style={{ fontSize: 20, fontWeight: "bold", marginVertical: 10 }}>Cart</Text>
            <FlatList 
                data={cart}
                keyExtractor={(item, index) => index.toString()}
                renderItem={({ item }) => (
                    <Text style={{ fontSize: 16, padding: 5 }}>{item}</Text>
                )}
            />
        </View>
    );
};

export default CoffeePickerView;
