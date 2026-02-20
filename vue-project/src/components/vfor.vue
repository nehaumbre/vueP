<!-- iterates over an array or object and renders a template 
 for each item in the collection
why use :key?
-Efficient DOM updates
 when vue renders list of elements it used virtual DOM to determine most 
 efficient way to update actual DOM
 key helps vue identify which elements have changed been added or removed
 without key vue may need to recreate entire DOM structure for each update which is not efficient
-Avoiding common pitfall
- duplicate key warnings in console
- incorrect key rendering when items are rearranged in list -->
<script setup>

import { ref } from 'vue';

const fruits = ref(['Mango', 'banana', 'apple', 'orange'])

const books = ref([
    {
        "id": 1,
        "title": "To Kill a Mockingbird",
        "author": "Harper Lee",
        "genre": "Fiction",
        "publishedYear": 1960,
        "available": true
    },
    {
        "id": 2,
        "title": "1984",
        "author": "George Orwell",
        "genre": "Dystopian",
        "publishedYear": 1949,
        "available": false
    },
    {
        "id": 3,
        "title": "The Great Gatsby",
        "author": "F. Scott Fitzgerald",
        "genre": "Classic",
        "publishedYear": 1925,
        "available": true
    },
    {
        "id": 4,
        "title": "The Hobbit",
        "author": "J.R.R. Tolkien",
        "genre": "Fantasy",
        "publishedYear": 1937,
        "available": true
    }
]
)

const movies = ref([
    ["The Shawshank Redemption", "The Godfather", "The Dark Knight"],
    ["Pulp Fiction", "Forrest Gump", "Fight Club"],
    ["Inception", "Interstellar", "The Matrix"],
    ["Gladiator", "The Lord of the Rings: The Fellowship of the Ring", "The Lion King"],
    ["Titanic", "Avatar", "The Avengers"],
    ["Jurassic Park", "The Silence of the Lambs", "Saving Private Ryan"],
    ["Braveheart", "The Departed", "Whiplash"],
    ["The Prestige", "Parasite", "Joker"],
    ["Spider-Man: Into the Spider-Verse", "The Social Network", "Mad Max: Fury Road"],
    ["La La Land", "The Green Mile", "Django Unchained"]
]
)

const games = ref({
    "game": {
        "title": "Legends of Valor",
        "genre": "Action RPG",
        "releaseYear": 2025,
        "developer": {
            "name": "NovaForge Studios",
            "founded": 2018,
            "location": {
                "city": "Los Angeles",
                "country": "USA"
            }
        },
        "platforms": ["PC", "PlayStation 5", "Xbox Series X"],
        "multiplayer": {
            "supported": true,
            "maxPlayers": 4,
            "modes": ["Co-op", "PvP Arena", "Ranked Matches"]
        },
        "systemRequirements": {
            "minimum": {
                "os": "Windows 10",
                "processor": "Intel i5",
                "ram": "8GB",
                "graphics": "GTX 1060",
                "storage": "50GB"
            },
            "recommended": {
                "os": "Windows 11",
                "processor": "Intel i7",
                "ram": "16GB",
                "graphics": "RTX 3060",
                "storage": "70GB SSD"
            }
        },
        "characters": [
            {
                "name": "Arin",
                "class": "Warrior",
                "levelCap": 60,
                "abilities": ["Slash", "Shield Block", "Berserk"]
            },
            {
                "name": "Lyra",
                "class": "Mage",
                "levelCap": 60,
                "abilities": ["Fireball", "Teleport", "Ice Storm"]
            }
        ],
        "inGameStore": {
            "currency": "Valor Coins",
            "microtransactions": true,
            "items": {
                "skins": ["Dragon Armor", "Shadow Cloak"],
                "boosts": ["XP Boost", "Gold Boost"]
            }
        },
        "ratings": {
            "esrb": "T",
            "userScore": 8.7,
            "criticScore": 9.1
        }
    }
}
)

const complexGamesObj = ref({
    game1: {
        title: 'Space Explorer',
        genre: 'Sci-Fi',
        platform: 'PC',
        releaseDate: '2023-05-20'
    },
    game2: {
        title: 'Fantasy Quest',
        genre: 'Fantasy',
        platform: 'PlayStation',
        releaseDate: '2023-07-10'
    },
    movie1: {
        title: 'Inception',
        director: 'Christopher Nolan',
        genre: 'Sci-Fi',
        releaseDate: '2010-07-16'
    },
    movie2: {
        title: 'The Shawshank Redemption',
        director: 'Frank Darabont',
        genre: 'Drama',
        releaseDate: '1994-09-23'
    },
    book1: {
        title: 'Dune',
        author: 'Frank Herbert',
        genre: 'Science Fiction',
        publicationYear: 1965
    },
    book2: {
        title: 'To Kill a Mockingbird',
        author: 'Harper Lee',
        genre: 'Fiction',
        publicationYear: 1960
    }
})

</script>

<template>
    <h1>VFOR</h1>
    <p v-for="(fruit, index) in fruits" :key="index">{{ index }}:{{ fruit }}</p>

    <!-- <ul v-for="({ id, title, author, genre, publishedYear, available }, index) in books" :key="index">
        <li>ID : {{ id }}</li>
        <li>TITLE : {{ title }}</li>
        <li>AUTHOR : {{ author }}</li>
        <li>genre : {{ genre }}</li>
        <li>publishedYear : {{ publishedYear }}</li>
        <li>available : {{ available }}</li>
    </ul>
    <ul v-for="(movie, index) in movies" :key="index">
        <li v-for="(m, index) in movie" :key="index">{{ m }}</li>
    </ul> -->
    <br>

    <!-- <ul v-for="(value,keys, index) in games" :key="value"> {{ index }} === {{ keys }}=== {{ value }}
        <li v-for="(val, k ,i) in value" :key ="val"> {{ i }} === {{ k}}=== {{ val }}</li>
    </ul> -->

    <ul v-for="(game, index) in complexGamesObj" :key="index">{{ game }}
        <li v-for="(property,key, index) in game" :key="index">{{key}}:{{ property }}</li>
    </ul>
    <ul v-for="num in 10" :key="num">
        <li>{{ num }}</li>
    </ul>
</template>