<template>
    <div>
        <svg
            @click="likeClicked"
            v-if="like == false"
            aria-label="좋아요"
            class="_8-yf5 "
            color="#262626"
            fill="#262626"
            height="24"
            role="img"
            viewBox="0 0 48 48"
            width="24"
        >
            <path
                d="M34.6 6.1c5.7 0 10.4 5.2 10.4 11.5 0 6.8-5.9 11-11.5 16S25 41.3 24 41.9c-1.1-.7-4.7-4-9.5-8.3-5.7-5-11.5-9.2-11.5-16C3 11.3 7.7 6.1 13.4 6.1c4.2 0 6.5 2 8.1 4.3 1.9 2.6 2.2 3.9 2.5 3.9.3 0 .6-1.3 2.5-3.9 1.6-2.3 3.9-4.3 8.1-4.3m0-3c-4.5 0-7.9 1.8-10.6 5.6-2.7-3.7-6.1-5.5-10.6-5.5C6 3.1 0 9.6 0 17.6c0 7.3 5.4 12 10.6 16.5.6.5 1.3 1.1 1.9 1.7l2.3 2c4.4 3.9 6.6 5.9 7.6 6.5.5.3 1.1.5 1.6.5.6 0 1.1-.2 1.6-.5 1-.6 2.8-2.2 7.8-6.8l2-1.8c.7-.6 1.3-1.2 2-1.7C42.7 29.6 48 25 48 17.6c0-8-6-14.5-13.4-14.5z"
            ></path>
        </svg>
        <svg
            @click="likeClicked"
            v-if="like == true"
            aria-label="좋아요 취소"
            class="_8-yf5 "
            color="#ed4956"
            fill="#ed4956"
            height="24"
            role="img"
            viewBox="0 0 48 48"
            width="24"
        >
            <path
                d="M34.6 3.1c-4.5 0-7.9 1.8-10.6 5.6-2.7-3.7-6.1-5.5-10.6-5.5C6 3.1 0 9.6 0 17.6c0 7.3 5.4 12 10.6 16.5.6.5 1.3 1.1 1.9 1.7l2.3 2c4.4 3.9 6.6 5.9 7.6 6.5.5.3 1.1.5 1.6.5s1.1-.2 1.6-.5c1-.6 2.8-2.2 7.8-6.8l2-1.8c.7-.6 1.3-1.2 2-1.7C42.7 29.6 48 25 48 17.6c0-8-6-14.5-13.4-14.5z"
            ></path>
        </svg>
    </div>
</template>

<script>
export default {
    props: ["post", "loginuser"],
    data() {
        return {
            like: false,
            userIdArray: []
        };
    },
    methods: {
        likeClicked() {
            // 서버에 like/unlike 요청 보내기.
            axios
                .post("/like/" + this.post.id)
                .then(res => {
                    console.log(res.data);
                    this.like = !this.like;
                })
                .catch(err => {
                    console.log(err);
                });
        },
        checkLikes() {
            /*
            tiis.post.likes가 현재 로그인한
            사용자의 아이디 즉, this.loginuser를 
            포함하고 있으면 
            like = true,
            그렇지 않으면 like = false
            */
            this.like = this.userIdArray.includes(this.loginuser);
        }
    },
    created() {
        this.userIdArray = this.post.likes.map(elem => {
            return elem.id;
        });
        this.checkLikes();
    }
};
</script>
