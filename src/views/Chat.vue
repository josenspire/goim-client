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
          <div id="list-view">
            <a-list :data-source="data">
              <a-list-item slot="renderItem" slot-scope="item, index">
                <a-list-item-meta :key="index">
                  <a slot="title" href="#">{{ item.name }}</a>
                  <a-avatar slot="avatar" :src="item.icon" />
                  <span slot="description">Ant Design, a design language for background applications, is refined by Ant UED Team</span>
                </a-list-item-meta>
              </a-list-item>
            </a-list>
          </div>
        </div>
      </div>
      <div class="right-panel">
        <div class="title">
          <span>James</span>
        </div>
        <div class="view-panel">
          <div class="msg-item left">
            <a-icon type="user" /> <span>How are your ?</span>
          </div>
          <div class="msg-item right">
            <span>I'm fine, thank you! And you?</span> <a-icon type="user" />
          </div>
          <div class="msg-item left">
            <a-icon type="user" /> <span>Fine.</span>
          </div>
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
  data () {
    return {
      data: [
        {
          id: "001",
          icon: "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES001",
        },
        {
          id: "002",
          icon: "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES002",
        },
        {
          id: "003",
          icon: "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES003",
        },
        {
          id: "004",
          icon: "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES004",
        },
        {
          id: "005",
          icon: "https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png",
          name: "JAMES005",
        },
      ],
    };
  }
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
    min-height: 120px;
    display: flex;
    min-width: 1024px;
    height: 760px;
    background-color: #f0f2f5;
    .left-panel {
      background-color: #fff;
      height: 100%;
      width: 35%;
      min-width: 120px;
      display: flex;
      #setting-bar {
        height: 100%;
        width: 70px;
        background-color: #1f1f1feb;
        padding: 20px 0px;
      }
      #list-panel {
        width: 100%;
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
        #list-view {
          width: 100%;
          height: 100%;
          overflow-x: hidden;
          overflow-y: auto;
          position: relative;
          // .user-item {
          //   background-color: #f5f5f5;
          //   color: #fff;
          //   height: 80px;
          //   line-height: 80px;
          // }
          ul>li {
            text-align: left;
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
          i {
            border: 1px solid #9c9c9c;
            padding: 5px;
            font-size: 24px;
            color: #000;
          }
          span {
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
          span {
            margin-left: 10px;
          }
        }
        .right {
          justify-content: flex-end;
          span {
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
