<script setup>

    
//   import {useApi} from '@/utils/api.ts';
  import { onMounted } from 'vue';
  import userImage from '@/components/plugins/UserImage.vue'
  import { useAuthStore } from '@/stores/auth.ts';


  const authStore = useAuthStore();
//   const categories = ref([]);
//   const dropdown = ref(false);


//   const toggleDropdown = () => {
//     dropdown.value = !dropdown.value
//   }

  const logout = () => {
    authStore.logout();
  };

  onMounted(() => {
    // useApi().get('/api/active-categories')
    //     .then((response) => {
    //         categories.value = response.data;
    //     })
  });

</script>

<template>
   <header class="header-navbar">
        <div class="container-xxl">
            <nav class="navbar navbar-expand navbar-light bg-light">
                <div class="container-fluid">
                    <router-link class="navbar-brand" to="/" target="_blank" :title="$t('site.Main page')">
                        <img src="/profile/images/vt-logo.png" alt="logo" width="36" height="36"/>
                    </router-link>
                    <form id="searchMember" class="searchMember navbar-search-group input-group d-none d-lg-flex">
                        <span class="input-group-text" id="basic-addon1">
                        <span class="material-icons size-font-ahalf"> search </span>
                        </span>
                        <input class="form-control navbar-search" type="text" name="search" placeholder="جستجو" aria-label="Search" id="dropdownSearch" data-bs-toggle="dropdown" aria-expanded="false"/>
                        <!-- <input id="searchLimit" class="form-control navbar-search" type="hidden" name="limit" value="50"/>
                        <input id="searchOffset"  class="form-control navbar-search" type="hidden" name="offset" value="0"/>
                        <div class="dropdown-menu is-right" aria-labelledby="dropdownSearch">
                            <div class="vt-dropdown-search">
                                <div class="search-list card-itemlist vt-dropdown-search-results">
                                    {{-- <a class="item align-baseline-force result-item">
                                        <div class="item-avatar">
                                            <img
                                                src="/assets/profile/images/users/gPZwCbdS.jpg"
                                                alt="user's avatar"
                                            />
                                        </div>
                                        <span>پرسپولیس</span>
                                    </a>
                                    <a class="result-item">
                                        <span>پاری سن ژرمن</span>
                                    </a>
                                    <a class="result-item">
                                        <span>پرز</span>
                                    </a>
                                    <a class="result-item">
                                        <span>پخش زنده</span>
                                    </a>
                                    <a class="result-item">
                                        <span>داریوش تاج پرست</span>
                                    </a> --}}
                                </div>


                                {{-- <div class="section-title">
                                    <span class="material-icons"> schedule </span>
                                    <span>تاریخچه جستجو</span>
                                </div>
                                <div class="vt-dropdown-search-history">
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> schedule </span>
                                        <span class="tag-name">مسی</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> schedule </span>
                                        <span class="tag-name">پرسپولیس</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> schedule </span>
                                        <span class="tag-name">رونالدو</span>
                                    </a>
                                </div>
                                <div class="section-title">
                                    <span class="material-icons"> local_fire_department </span>
                                    <span>داغ ترینها</span>
                                </div>
                                <div class="vt-dropdown-search-trends">
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> tag </span>
                                        <span class="tag-name">استقلال</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> tag </span>
                                        <span class="tag-name">پرسپولیس</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> tag </span>
                                        <span class="tag-name">تراکتورسازی</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> tag </span>
                                        <span class="tag-name">مسی</span>
                                    </a>
                                    <a class="btn btn-primary search-tag" href="#">
                                        <span class="material-icons tag-icon"> tag </span>
                                        <span class="tag-name">داربی</span>
                                    </a>
                                </div> --}}
                            </div>
                        </div> -->
                    </form>

                    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                        <span class="navbar-toggler-icon"></span>
                    </button>

                    <div class="navbar-collapse justify-content-end" id="navbarSupportedContent">
                        <ul class="navbar-nav mb-lg-2 mb-lg-0">
                            <li class="nav-item dropdown d-block d-lg-none">
                                <button
                                    class="btn btn-light"
                                    type="button"
                                    id="dropdownMobileSearch"
                                    data-bs-toggle="dropdown"
                                    aria-expanded="false"
                                >
                                    <span class="material-icons size-font-ahalf"> search </span>
                                </button>

                                <div class="dropdown-menu is-left" aria-labelledby="dropdownMobileSearch">
                                    <div class="vt-dropdown-search">
                                        <div class="input-group w-full">
                                            <span class="input-group-text" id="basic-addon1">
                                            <span class="material-icons size-font-ahalf">
                                                search
                                            </span>
                                            </span>
                                            <form class="searchMember">
                                                <input class="form-control navbar-search" type="search" placeholder="جستجو" aria-label="Search" id="dropdownSearch" data-bs-toggle="dropdown" aria-expanded="false"/>
                                            </form>
                                        </div>
                                        <!-- <div class="search-list card-itemlist vt-dropdown-search-results"> -->
                                            <!-- {{-- <a class="result-item">
                                                <span>پرسپولیس</span>
                                            </a>
                                            <a class="result-item">
                                                <span>پاری سن ژرمن</span>
                                            </a>
                                            <a class="result-item">
                                                <span>پرز</span>
                                            </a>
                                            <a class="result-item">
                                                <span>پخش زنده</span>
                                            </a>
                                            <a class="result-item">
                                                <span>داریوش تاج پرست</span>
                                            </a> --}}
                                        </div>
                                        {{-- <div class="section-title">
                                            <span class="material-icons"> schedule </span>
                                            <span>تاریخچه جستجو</span>
                                        </div> -->
                                        <div class="vt-dropdown-search-history flex-wrap">
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon">
                                                    schedule
                                                </span>
                                                <span class="tag-name">مسی</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon">
                                                    schedule
                                                </span>
                                                <span class="tag-name">پرسپولیس</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon">
                                                    schedule
                                                </span>
                                                <span class="tag-name">رونالدو</span>
                                            </a>
                                        </div>
                                        <div class="section-title">
                                            <span class="material-icons">
                                            local_fire_department
                                            </span>
                                            <span>داغ ترینها</span>
                                        </div>
                                        <div class="vt-dropdown-search-trends flex-wrap">
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon"> tag </span>
                                                <span class="tag-name">استقلال</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon"> tag </span>
                                                <span class="tag-name">پرسپولیس</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon"> tag </span>
                                                <span class="tag-name">تراکتورسازی</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon"> tag </span>
                                                <span class="tag-name">مسی</span>
                                            </a>
                                            <a class="btn btn-primary search-tag" href="#">
                                                <span class="material-icons tag-icon"> tag </span>
                                                <span class="tag-name">داربی</span>
                                            </a>
                                        </div>
                                    </div>
                                </div>
                            </li>
                            <li class="nav-item dropdown">
                                <button
                                    class="btn btn-light"
                                    type="button"
                                    id="dropdownNotifications"
                                    data-bs-toggle="dropdown"
                                    aria-expanded="false"
                                >
                                    <span class="material-icons size-font-ahalf">
                                    notifications
                                    </span>
                                </button>
                                <div
                                    class="dropdown-menu is-left"
                                    aria-labelledby="dropdownNotifications"
                                >
                                    <div class="vt-dropdown-notification-reel">
                                        <div class="notification">
                                            <a href="#" class="stretched-link"></a>
                                            <div class="notification-avatar-container">
                                                <img class="inline" v-if="authStore?.user?.profile_photo_path?.length > 0" :src="authStore?.user?.profile_photo_path" :alt="authStore?.user?.nickname" />
                                                <img class="inline" v-else src="/assets/site/images/user-icon.png" :alt="authStore?.user?.nickname" />
                                            </div>
                                            <div class="notification-info-container">
                                                <div class="notification-actor">مهرداد کردی</div>
                                                <div class="notification-date">2 ساعت پیش</div>
                                                <div class="notification-action">
                                                    یک خبر را به اشتراک گذاشت
                                                </div>
                                                <div class="notification-details">
                                                    لیونل مسی، ستاره آرژانتینی دنیای فوتبال سرانجام و پس
                                                    از 20 سال حضور در نیوکمپ، بارسلونا را ترک کرد و پاری
                                                    سن ژرمن پیوست. در این ویدیو که کاری از تیفو فوتبال
                                                    است به آمار و رکوردهای این بازیکن پرداخته شده است.
                                                </div>
                                            </div>
                                        </div>
                                        <div class="notification">
                                            <a href="#" class="stretched-link"></a>
                                            <div class="notification-avatar-container">
                                                <img
                                                    src="/assets/profile/images/users/pexels-photo-764529.jpeg"
                                                    alt=""
                                                />
                                            </div>
                                            <div class="notification-info-container">
                                                <div class="notification-actor">احمد بارسلونا</div>
                                                <div class="notification-date">3 ساعت پیش</div>
                                                <div class="notification-action">
                                                    نظر شما را لایک کرد
                                                </div>
                                                <div class="notification-details">
                                                    لیونل مسی، ستاره آرژانتینی دنیای فوتبال سرانجام و پس
                                                    از 20 سال حضور در نیوکمپ، بارسلونا را ترک کرد و پاری
                                                    سن ژرمن پیوست. در این ویدیو که کاری از تیفو فوتبال
                                                    است به آمار و رکوردهای این بازیکن پرداخته شده است.
                                                </div>
                                            </div>
                                        </div>
                                        <div class="notification">
                                            <a href="#" class="stretched-link"></a>
                                            <div class="notification-avatar-container">
                                                <img
                                                    src="/assets/profile/images/users/gPZwCbdS.jpg"
                                                    alt=""
                                                />
                                            </div>
                                            <div class="notification-info-container">
                                                <div class="notification-actor">احمد بارسلونا</div>
                                                <div class="notification-date">3 ساعت پیش</div>
                                                <div class="notification-action">
                                                    نظر شما را لایک کرد
                                                </div>
                                                <div class="notification-details">
                                                    لیونل مسی، ستاره آرژانتینی دنیای فوتبال سرانجام و پس
                                                    از 20 سال حضور در نیوکمپ، بارسلونا را ترک کرد و پاری
                                                    سن ژرمن پیوست. در این ویدیو که کاری از تیفو فوتبال
                                                    است به آمار و رکوردهای این بازیکن پرداخته شده است.
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="vt-dropdown-executables">
                                        <button class="btn btn-primary is-full">
                                            مشاهده تمام اعلان ها
                                        </button>
                                    </div>
                                </div>
                            </li>
                            <li class="nav-item dropdown user-dropdown">
                                <button
                                    class="btn btn-light dropdown-toggle"
                                    type="button"
                                    id="dropdownProfile"
                                    data-bs-toggle="dropdown"
                                    aria-expanded="false"
                                >
                                    <div class="profile-avatar">
                                        <userImage add-class="inline" :item="authStore?.user" />
                                    </div>
                                    <span class="user-name">{{ authStore?.user?.nickname }}</span>
                                </button>
                                <div
                                    class="dropdown-menu is-left"
                                    aria-labelledby="dropdownProfile"
                                >
                                    <div class="vt-dropdown-list-menu">
                                        <a class="vt-list-menu-item" href="#" :title="$t('site.Profile')">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> account_circle </span>
                                            </span>
                                            <span class="dropdown-item-title">{{ $t('site.Profile') }}</span>
                                        </a>

                                        <a class="vt-list-menu-item" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> bookmark </span>
                                            </span>
                                            <span class="dropdown-item-title">ذخیره شده</span>
                                        </a>

                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> manage_accounts </span>
                                            </span>
                                            <span class="user-link-title">
                                            ویرایش حساب کاربری
                                            </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> group_add </span>
                                            </span>
                                            <span class="user-link-title">
                                            درخواست های دنبال کردن
                                            </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> chat </span>
                                            </span>
                                            <span class="user-link-title"> پیام های خصوصی </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> verified_user </span>
                                            </span>
                                            <span class="user-link-title"> تایید حساب کاربری </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> paid </span>
                                            </span>
                                            <span class="user-link-title">
                                            ارتقاع حساب کاربری
                                            </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                                <span class="material-icons"> article </span>
                                            </span>
                                            <span class="user-link-title"> مدیریت مطالب </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                                <span class="material-icons"> post_add </span>
                                            </span>
                                            <span class="user-link-title"> ایجاد مطالب جدید </span>
                                        </a>
                                        <a class="vt-list-menu-item is-mobile" href="#">
                                            <span class="dropdown-item-icon">
                                                <span class="material-icons"> block </span>
                                            </span>
                                            <span class="user-link-title"> مسدود شده ها </span>
                                        </a>

                                        <a class="vt-list-menu-item" href="#">
                                            <span class="dropdown-item-icon">
                                            <span class="material-icons"> settings </span>
                                            </span>
                                            <span class="dropdown-item-title">تنظیمات</span>
                                        </a>

                                        <div class="vt-list-menu-divider"></div>
                                        <a @click="logout" lass="vt-list-menu-item">
                                            <span class="dropdown-item-icon">
                                                <span class="material-icons">
                                                    power_settings_new
                                                </span>
                                            </span>
                                            <span class="dropdown-item-title">{{ $t('site.Logout') }}</span>
                                        </a>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </nav>
        </div>
    </header>

</template>
