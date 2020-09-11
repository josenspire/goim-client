<template>
  <div class="container">
    <div class="content">
      <div class="left-panel">
        <div id="setting-bar">
          <a-avatar style="color: #f56a00; backgroundColor: #fde3cf">
            U
          </a-avatar>
        </div>
        <div id="list-panel">
          <div class="title">
            <a-input type="text" placeholder="Search" />
          </div>
          <div class="list-view">
            <ul>
              <li
                v-for="(item, index) in data"
                :key="index"
                @click="switchChatWindows(item)"
                class="u-item"
                :class="{ active: isActive(item.id) }"
              >
                <a-avatar :src="item.icon" class="u-icon"></a-avatar>
                <div class="u-prof">
                  <h4>
                    <span id="u-name">{{ item.name }}</span>
                  </h4>
                  <div id="u-desc">
                    Ant Design, a design language for background applications,
                    is refined by Ant UED Team
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="right-panel">
        <div class="title">
          <span>{{ selectedContact.name }}</span>
        </div>
        <div class="view-panel">
          <div
            v-for="(item, index) in targetChatList"
            :key="index"
            class="msg-item"
            :class="isSendMessage(item.messageDirection) ? 'right' : 'left'"
          >
            <template v-if="isSendMessage(item.messageDirection)">
              <span class="msg-content">{{item.content}}</span> <a-avatar style="backgroundColor:#87d068" icon="user" size="48"/>
            </template>
            <template v-else>
              <a-avatar :src="userProfile.icon" /> <span class="msg-content">{{item.content}}</span>
            </template>
          </div>
          <!-- <div class="msg-item left">
            <a-icon type="user" /> <span>How are your ?</span>
          </div>
          <div class="msg-item right">
            <span>I'm fine, thank you! And you?</span> <a-icon type="user" />
          </div>
          <div class="msg-item left">
            <a-icon type="user" /> <span>Fine.</span>
          </div> -->
        </div>
        <div class="ops-panel">
          <div class="input-panel">
            <a-textarea placeholder="Basic usage" :rows="1" />
          </div>
          <div class="footer">
            <a-button type="primary">Send</a-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
  data() {
    return {
      userProfile: {
        id: "001",
        name: "JAMES001",
        icon:
          "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
      },
      selectedContact: {},
      data: [],
      selectedChat: {
        "009": [
          {
            id: "msg001",
            type: "SINGLE_CHAT",
            targetId: "001",
            senderUserId: "009",
            content: "How are you?",
            messageType: "MESSAGE",
            messageDirection: "2", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-11T09:10:12+08:00",
            receivedTime: "2020-09-11T09:10:19+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
          {
            id: "msg002",
            type: "SINGLE_CHAT",
            targetId: "009",
            senderUserId: "001",
            content: "I am fine thank you, and you?",
            messageType: "MESSAGE",
            messageDirection: "1", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-11T09:10:30+08:00",
            receivedTime: "2020-09-11T09:10:34+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
          {
            id: "msg001",
            type: "SINGLE_CHAT",
            targetId: "001",
            senderUserId: "009",
            content: "Fine...",
            messageType: "MESSAGE",
            messageDirection: "2", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-11T09:10:55+08:00",
            receivedTime: "2020-09-11T09:11:00+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
        ],
        "005": [
          {
            id: "msg003",
            type: "SINGLE_CHAT",
            targetId: "005",
            senderUserId: "001",
            content: "Let's going to the party?",
            messageType: "MESSAGE",
            messageDirection: "1", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-10T20:12:12+08:00",
            receivedTime: "2020-09-10T20:12:15+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
          {
            id: "msg004",
            type: "SINGLE_CHAT",
            targetId: "001",
            senderUserId: "005",
            content: "That's great, what's time is it?",
            messageType: "MESSAGE",
            messageDirection: "2", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-10T20:13:50+08:00",
            receivedTime: "2020-09-10T20:14:20+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
          {
            id: "msg005",
            type: "SINGLE_CHAT",
            targetId: "005",
            senderUserId: "001",
            content: "On 21:00, let's going now.",
            messageType: "MESSAGE",
            messageDirection: "1", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-10T20:14:12+08:00",
            receivedTime: "2020-09-10T20:14:15+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
          {
            id: "msg006",
            type: "SINGLE_CHAT",
            targetId: "001",
            senderUserId: "005",
            content: "OK, see you late.",
            messageType: "MESSAGE",
            messageDirection: "2", // 1：发送，2：接收
            isOfflineMessage: false, // 是否离线消息
            sentTime: "2020-09-10T20:13:50+08:00",
            receivedTime: "2020-09-10T20:14:20+08:00",
            isPersited: true, // 消息是否存在客户端
            isCounted: false, // 消息是否计数
          },
        ],
      },
    };
  },
  created() {
    this.initialUserList();
  },
  computed: {
    targetChatList() {
      return this.selectedChat[this.selectedContact.id];
    },
  },
  methods: {
    initialUserList() {
      const results = [];
      for (let i = 0; i < 20; i++) {
        results.push({
          id: "00" + i,
          icon:
            "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES00" + i,
        });
      }
      this.data = Object.assign([], results);
    },
    switchChatWindows(targetUser) {
      this.selectedContact = Object.assign({}, targetUser);
      console.log(targetUser);
    },
    isActive(targetUserId) {
      return targetUserId === this.selectedContact.id;
    },
    isSendMessage (direction) {
      return direction == "1";
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  .content {
    border: 1px solid #f0f2f5;
    color: #ffffff;
    display: flex;
    width: 1024px;
    height: 760px;
    min-height: 120px;
    background-color: #f0f2f5;
    .left-panel {
      background-color: #fff;
      height: 100%;
      width: 35%;
      min-width: 120px;
      display: flex;
      #setting-bar {
        height: 100%;
        width: 60px;
        background-color: #1f1f1feb;
        padding: 20px 0px;
      }
      #list-panel {
        width: calc(100% - 60px);
        display: flex;
        flex-wrap: wrap;
        .title {
          display: flex;
          justify-content: center;
          align-items: center;
          background: #f5f5f5;
          height: 58px;
          width: 100%;
          padding: 20px 0 10px 0;
          input {
            width: 80%;
            height: 30px;
          }
        }
        .list-view {
          display: flex;
          width: 100%;
          height: calc(100% - 58px);
          overflow-x: hidden;
          overflow-y: auto;
          flex-wrap: wrap;
          background-color: #f5f5f5;

          &::-webkit-scrollbar {
            width: 6px; /*高宽分别对应横竖滚动条的尺寸*/
            height: 6px;
          }
          &::-webkit-scrollbar-thumb {
            border-radius: 6px;
            background: rgba(144, 147, 153, 0.5);
          }
          &::-webkit-scrollbar-track {
            border-radius: 5px;
            background: transparent;
          }

          ul {
            margin: 0;
            padding: 0;
            li {
              cursor: pointer;
              &:not(.active):hover {
                background-color: #f1f1f1;
              }
            }
            .active {
              background-color: #d9d9d9;
            }
          }

          .u-item {
            display: flex;
            align-items: center;
            border-bottom: 1px solid #9c9c9c17;
            padding: 15px 10px;
            background-color: #f5f5f5;

            .u-icon {
              font-size: 20px;
              display: inline-flex;
            }
            .u-prof {
              display: inline-flex;
              flex-wrap: wrap;
              margin-left: 10px;
              h4 {
                width: 100%;
                text-align: left;
              }
              #u-name {
                font-size: 14px;
                color: #000;
                display: block;
              }
              #u-desc {
                font-size: 12px;
                color: #9c9c9c;
                display: block;
                width: 120px;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
              }
            }
          }
        }
      }
    }
    .right-panel {
      background-color: #f0f2f5;
      width: 75%;
      height: 100%;
      .title {
        font-size: 20px;
        font-weight: 600;
        text-align: left;
        color: #000;
        background-color: #fcfcfc;
        height: 40px;
        display: flex;
        align-items: center;
        padding: 10px 20px;
      }
      .view-panel {
        height: 65%;
        background-color: #fcfcfc;
        overflow-x: hidden;
        overflow-y: auto;
        padding: 5px 10px;
        border-top: 1px solid #f1f1f1;
        border-bottom: 1px solid #f1f1f1;
        .msg-item {
          margin: 10px 0;
        }
        .left,
        .right {
          display: flex;
          align-items: center;
          width: 100%;
          height: 40px;
          // img {
          //   border: 1px solid #9c9c9c;
          //   padding: 5px;
          //   font-size: 24px;
          //   color: #000;
          // }
          .msg-content {
            display: flex;
            align-items: center;
            height: 100%;
            min-width: 70px;
            padding: 0 10px;
            border-radius: 0.4em;
            background: green;
            opacity: 0.8;
          }
        }
        .left {
          justify-content: flex-start;
          .msg-content {
            margin-left: 10px;
          }
        }
        .right {
          justify-content: flex-end;
          .msg-content {
            margin-right: 10px;
          }
        }
      }
      .ops-panel {
        background-color: #ffffff;
        height: calc(35% - 40px);
        .input-panel {
          width: 100%;
          .ant-input {
            width: 100%;
            height: 160px;
            border: none;
            &:focus {
              box-shadow: none;
              border: none;
            }
          }
        }
        .footer {
          width: 100%;
          height: auto;
          padding: 10px 10px;
          text-align: right;
        }
      }
    }
  }
}
</style>
