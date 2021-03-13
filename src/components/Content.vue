<template>
    <div class="container">
        <Header-div>
            <svg xmlns="http://www.w3.org/2000/svg" width="1366" height="156"><g fill="#63BABA" fill-rule="evenodd"><path d="M470.577 563.429c-51.432-51.425-51.438-134.806-.013-186.237l.013-.013L867.235-19.424c51.441-51.434 134.836-51.434 186.276 0 48.811 48.804 51.304 126.392 7.473 178.135l178.158-178.135c51.441-51.434 134.836-51.434 186.277 0 51.431 51.424 51.437 134.805.013 186.237-.005.004-.01.008-.013.013l-396.66 396.603c-51.44 51.433-134.834 51.433-186.275 0-48.812-48.805-51.304-126.394-7.471-178.138L656.853 563.43c-51.441 51.433-134.836 51.433-186.276 0zM342.268 45.605c-51.432-51.425-51.438-134.806-.013-186.237l.013-.013 396.658-396.603c51.441-51.434 134.836-51.434 186.277 0 51.431 51.424 51.437 134.805.013 186.237-.005.004-.01.008-.013.013L528.543 45.605c-51.44 51.433-134.834 51.433-186.275 0zm-444.692 71.824c-51.432-51.424-51.438-134.806-.013-186.237l.013-.013 396.658-396.603c51.441-51.434 134.836-51.434 186.277 0 51.431 51.424 51.437 134.805.013 186.237a80.86 80.86 0 01-.013.013L83.85 117.429c-51.44 51.433-134.834 51.433-186.275 0z"/></g></svg>
        </Header-div>

        <input type="text" v-model="filterStack" @keyup.enter="returnFilterStack">
        <div class="content"
        v-for="data in data"
        :key="data.id" 
        :class="{bind: data.featured==true}">

            <div class="job-profile">
                <div class="img-div">
                    <img 
                    :src="require(`@/assets/images/${data.logo}`)" 
                    :alt="data.logo">
                </div>
                <div class="job-profile-deets">
                    <ul class="div-one">
                        <li class="company">{{data.company}}</li>
                        <li class="new" v-if="data.new == true">NEW!</li>
                        <li class="featured" v-if="data.featured == true ">FEATURED</li>
                    </ul>
                    <p class="position">{{data.position}}</p>
                    <ul class="div-two">
                        <li>{{data.postedAt}}</li>
                        <li>{{data.contract}}</li>
                        <li>{{data.location}}</li>
                    </ul>
                </div>
            </div>

            <ul class="filter-div" >
                <li>{{data.role}}</li>
                <li>{{data.level}}</li>
                <li v-for="(lang , index) in data.languages" 
                :key="index"
                >
                {{lang}}
                </li>
            </ul>

        </div>
    </div>
</template>

<script>

import usersData from "/data.json"

import HeaderDiv from './Header.vue'

export default {

    components: {
        HeaderDiv
    },
    data(){
        return{
            data:usersData,
            filterStack: ""
        }
    },
    methods:{
        returnFilterStack(){
            // console.log("rice")
            let stack = []
            this.data.forEach(data => {
                if(data.languages.includes(this.filterStack)|| data.role.includes(this.filterStack) || data.level.includes(this.filterStack)){
                    stack.push(data)
                }
            });
            this.data = stack;
        },
    },
    computed:{
      
    }
}
</script>

<style lang="scss" scoped>

.container{
    background-color:#f0fafb;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: 15px;

    .content{
        margin:20px;
        display:flex;
        align-items: center;
        justify-content: space-between;
        padding: 10px;
        width:75%;
        border-radius: 5px;
        background-color:#fff;
        box-shadow: 3px 3px 10px 2px #d6ebee;

        .job-profile{
            display: flex;
            align-items: center;
            padding-bottom: 20px;
            
                .img-div{
                    width: 100px;
                }

                .job-profile-deets{
                    display: flex; 
                    flex-direction: column;

                    >*{
                    padding-top: 12px;
                    }

                    p{
                        font-weight: 700;
                        font-size: 20px;
                    }

                    .div-one{
                        list-style-type: none;
                        font-weight: 700;

                        .company{
                            color:hsl(179, 29%, 51%);
                        }

                        .new{
                            background: hsl(179, 29%, 51%);
                            color: #fff;
                            border-radius: 20px;
                            padding: 5px 10px ;
                        }
    
                        .featured{
                            background: rgb(77, 75, 75);
                            color: #fff;
                            border-radius: 20px;
                            padding: 5px 10px;
                        } 
                    }

                    .div-two{
                        color: rgb(148, 147, 147);
                        list-style-type: decimal;
                    }

                    p{
                        margin: 0;
                    }
                }
            }

            .filter-div{
                    display:flex;
                li{
                    background-color: #f1f7f5;
                    padding: 6px;
                    border-radius: 3px;
                    font-weight: 700;
                    color: #749799;
                }
            }
        }
    }

.bind{
    border-left:6px solid hsl(179, 29%, 51%)
}

svg{
    width:100%;
    background-color: #5da5a4;
}

ul{
    padding:0;
    margin:0;
}

ul li{
    display:inline;
    margin-right: 15px;
}

@media(max-width: 1000px){

    .content{
        display: flex;
        flex-direction: column;
        .job-profile{
            border-bottom:2px solid #ccc;
        }
        .filter-div{
            padding: 10px;
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;
            li{
                margin-bottom: 10px;
            }
        }
    }
}

</style>