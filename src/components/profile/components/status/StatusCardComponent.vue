<script setup>

  import {useApi} from '@/utils/api.ts';
  import { onMounted, defineProps, ref } from 'vue';
  import userImage from '@/components/plugins/UserImage.vue';
  import CommentWallComponent from '../comment/CommentWallComponent.vue';
  import CommentWallFormComponent from '../comment/CommentWallFormComponent.vue';
  import { useAuthStore } from '@/stores/auth.ts';

    const authStore = useAuthStore();

    const props =  defineProps({
        status: {
            type: Object,
            require: true
        }
    });

    const isActive = ref(false)
    const commentActive = ref(false)
    const comments = ref([])
    const likeCount = ref(props.status?.likes?.length)

    const likeStatus = (id) => {
        useApi().post('/api/like', {
            id: id,
            type: 'status'
        })
        .then((response) => {
            if (response.data.status == 1) {
                isActive.value = response.data.active;
                likeCount.value = response.data.count;
            }
        })
    }

    const commentToggle = (id) => {
        commentActive.value = !commentActive.value

        if (commentActive.value && comments.value.length == 0) {
            useApi().get(`/api/comment/status/${id}`)
                .then((response) => {
                    comments.value = response.data;
                });
        }
    }

    const checkLike = () => {
        if (props.status?.likes?.length > 0) {
            let user = props.status?.likes.find(item => item.user_id == authStore.user.id);
            if (user) {
                isActive.value = true;
            }
        }
    }

    const updateComments = (id) => {
        useApi().get(`/api/comment/status/${id}`)
                .then((response) => {
                    comments.value = response.data;
                });
    }
    
    onMounted(() => {
        checkLike();
    });
</script>

<template>
    <div class="card-body">
        <div class="tweet-user-avatar">
            <userImage :item="status?.user" />
        </div>
        <div class="tweet-info">
            <div class="tweet-info-head">
                <span class="tweet-user-name">{{ status?.user?.nickname }}</span>
                <span class="tweet-date">{{ status?.created_at }}</span>
            </div>
            <div class="tweet-body">
                {{ status?.text }}
                <img v-if="status?.file?.length > 0" :src="status.file"/>
            </div>
        </div>
        <div class="tweet-exes">
            <button @click="likeStatus(status.id)" :class="{
                'btn btn-light': true,
                'is-active': isActive
                }">
                <svg aria-hidden="true" focusable="false" data-prefix="fas" data-icon="thumbs-up" class="svg-inline--fa fa-thumbs-up fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <path fill="currentColor" d="M104 224H24c-13.255 0-24 10.745-24 24v240c0 13.255 10.745 24 24 24h80c13.255 0 24-10.745 24-24V248c0-13.255-10.745-24-24-24zM64 472c-13.255 0-24-10.745-24-24s10.745-24 24-24 24 10.745 24 24-10.745 24-24 24zM384 81.452c0 42.416-25.97 66.208-33.277 94.548h101.723c33.397 0 59.397 27.746 59.553 58.098.084 17.938-7.546 37.249-19.439 49.197l-.11.11c9.836 23.337 8.237 56.037-9.308 79.469 8.681 25.895-.069 57.704-16.382 74.757 4.298 17.598 2.244 32.575-6.148 44.632C440.202 511.587 389.616 512 346.839 512l-2.845-.001c-48.287-.017-87.806-17.598-119.56-31.725-15.957-7.099-36.821-15.887-52.651-16.178-6.54-.12-11.783-5.457-11.783-11.998v-213.77c0-3.2 1.282-6.271 3.558-8.521 39.614-39.144 56.648-80.587 89.117-113.111 14.804-14.832 20.188-37.236 25.393-58.902C282.515 39.293 291.817 0 312 0c24 0 72 8 72 81.452z"></path>
                </svg>
                <span>{{ likeCount }}</span>
            </button>
            <button class="btn btn-light" @click="commentToggle(status.id)">
                <svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="comment" class="svg-inline--fa fa-comment fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
                    <path fill="currentColor" d="M256 32C114.6 32 0 125.1 0 240c0 47.6 19.9 91.2 52.9 126.3C38 405.7 7 439.1 6.5 439.5c-6.6 7-8.4 17.2-4.6 26S14.4 480 24 480c61.5 0 110-25.7 139.1-46.3C192 442.8 223.2 448 256 448c141.4 0 256-93.1 256-208S397.4 32 256 32zm0 368c-26.7 0-53.1-4.1-78.4-12.1l-22.7-7.2-19.5 13.8c-14.3 10.1-33.9 21.4-57.5 29 7.3-12.1 14.4-25.7 19.9-40.2l10.6-28.1-20.6-21.8C69.7 314.1 48 282.2 48 240c0-88.2 93.3-160 208-160s208 71.8 208 160-93.3 160-208 160z"></path>
                </svg>
                <span>{{ status?.comments }}</span>
            </button>
        </div>
        <div v-if="commentActive" class="tweet-comments">
            <CommentWallFormComponent @updateComments="updateComments(status.id)" :model-id="status.id" model-type="status" />
            <CommentWallComponent @updateComments="updateComments(status.id)" :comments="comments" :model-id="status.id" model-type="status"/>
        </div>
    </div>
</template>