<template>
    <div class="movie__search">
        <h2 class="blind">검색하기</h2>
        <input type="search" v-model="searchTerm" @keyup.enter="search" placeholder="검색어를 입력해주세요!">
        <button type="submit" @click="search">검색</button>
    </div>
</template>


<script>
export default {

}
</script>