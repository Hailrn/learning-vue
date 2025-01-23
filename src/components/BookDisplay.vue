<template>
    <div class="book-container">
        <table border="1" style="border-collapse: collapse;">
            <thead>
                <tr>
                    <th>Title</th>
                    <th>Author</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(buku, index) in koleksiBuku" :key="index">
                    <td>{{ buku.title }}</td>
                    <td>{{ buku.author }}</td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <td colspan="2">
                        Total Buku: {{ koleksiBuku.length }}
                    </td>
                </tr>
            </tfoot>
        </table>
    </div>
</template>

<script>
export default {
    name: 'BookDisplay',
    data() {
        return {
            koleksiBuku: [
                { title: "To Kill a Mockingbird", author: "Harper Lee" },
                { title: "1984", author: "George Orwell" },
                { title: "The Great Gatsby", author: "F. Scott Fitzgerald" },
                { title: "Moby Dick", author: "Herman Melville" },
                { title: "Pride and Prejudice", author: "Jane Austen" }
            ]
        }
    },
}
</script>

<style>
table {
    width: 100%;
    border: 1px solid #ddd;
}

th, td {
    padding: 10px 30px;
}

th {
    background-color: #f4f4f4;
}

td {
    text-align: center;
}
</style>