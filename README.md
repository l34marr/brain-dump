# Quick Notes

to make my brain more peaceful

# conda

conda create --name myenv python=3.8
conda install -n myenv scipy=0.15.0
conda install -n myenv --file spec-file.txt
想要的程式最好一次全列才能避免相依狀態混亂
conda list --explicit > spec-file.txt
.condarc 可以建立 create_default_packages
conda env list
conda env create -f environment.yml
conda activate myenv

# pipenv

  $ mkdir DjangoReact
  $ cd DjangoReact
  $ pipenv --three

起始環境只有 Pipfile 檔案，依照 pipenv install pkg_name 或 pipenv install pkg_name --dev 來安裝開發階段的模組。

[[source]]
url = "https://pypi.python.org/simple"
verify_ssl = true
name = "pypi"

[packages]

[dev-packages]

[requires]
python_version = "3.8"

實際有模組安裝後，會產生 Pipfile.lock 檔案，內含相依模組的 hash 值，比 requirements.txt 來得更有保障。

$ pipenv run python myscript.py

根據 virtualenv 執行相關 Python 指令，但不進入虛擬環境。

$ pipenv shell

類似 source venv/bin/activate 進入虛擬環境，就可以再用 pipenv install 安裝需要的模組。

範例文件 https://www.digitalocean.com/community/tutorials/build-a-to-do-application-using-django-and-react

$ pipenv install django
$ django-admin startproject backend

$ cd backend
$ python manage.py startapp todo
$ python manage.py migrate
$ python manage.py runserver

在 settings.py 註冊 todo 應用程式，再到 models.py 修改 Model 定義。

# React

在純 React 或 Flux 應用程式裡，建議將 state 盡可能儲存在幾個物件中。
使用 Redux 時，我們將 state 管理從 React 中完全抽出，由 Redux 管理，它要求將所有 state 集中在單一不可變的物件中。

obj
+-- {user}
+-- [messages] -- {message}, {message}
+-- editMessage
+-- [expandedMessage]
+-- [posts] -- {post}, {post}
+-- [postsSeen]

建構 Redux 應用程式時，第一件事是考慮 state 嘗試將它定義在單一物件中。接著再透過 action 更新 state 並記錄異動歷史。
如果物件導向設計是名詞導向，在 Redux 思惟裡是動詞導向，辨識出 action 後，可以將它們列在 constants.js 檔案裡。
action 是提供 state 改變的指令之 JavaScript 實字，大部份的異動也需要一些資料，這種資料稱為 action 的酬載。
狀態樹儲存在單一物件中，想要達到模組化的效果，是透過函式來做到，這些函式稱為 reducer。
它是以目前狀態與 action 作為參數建構，並回傳新狀態的函式，它用於更新狀態樹的葉或分支，可以組合多個 reducer 到一個 reducer 中來處理整個 state 的更新。

export const color = (state = {}, action) => {
    switch (action.type) {
        case C.ADD_COLOR:
            return {
                id: action.id,
                title: action.title,
                color: action.color,
                timestamp: action.timestamp,
                rating: 0
            }
        case C.RATE_COLOR:
            return (state.id !== action.id) ?
                state:
                {
                    ...state,
                    rating: action.rating
                }
        default:
            return state
    }
}

以下是 color 的 action

store.dispatch({
    type: "RATE_COLOR",
    id: "2222e1p5",
    rating: 5
})

store 的 subscribe 方法回傳之後可供取消傾聽程式訂閱的函式：
const logState = () => console.log('next state', store.getState())
const unsubscribeLogger = store.subscribe(logState)
// cancel subscrib
unsubscribeLogger()

使用 Local Store

const store = createStore(
    combineReducers({ colors, sort }),
    (localStorage['redux-store']) ?
        JSON.parse(localStorage['redux-store']) :
        {}
)
store.subscribe(() => {
  localStorage['redux-store'] = JSON.stringify(store.getState())
})
console.log('current color count', store.getState().colors.length)
console.log('current state', store.getState())
store.dispatch({
    type: "ADD_COLOR",
    id: uuid.v4(),
    title: "Party Pink",
    color: "#F142FF",
    timestamp: new Date().toString()
})

建構 store 時，我們建構中介軟體的兩個部份: logger, saver
資料透過中介軟體而非 store 方法儲存到 localStore

storeFactory: ./store/index.js

import { createStore,
         combineReducers,
         applyMiddleware } from 'redux'
import { colors, sort } from './reducers'
import stateData from './initialState'

const logger = store => next => action => {
    let result
    console.groupCollapsed("dispatching", action.type)
    console.log('prev state', store.getState())
    console.log('action', action)
    result = next(action)
    console.log('next state', store.getState())
    console.groupEnd()
}

const saver = store => next => action => {
    let result = next(action)
    localStorage['redux-store'] = JSON.stringify(store.getState())
    return result
}

const storeFactory = (initialState=stateData) =>
    applyMiddleware(logger, saver)(createStore)(
    combineReducers({colors, sort}),
    (localStorage['redux-store']) ?
        JSON.parse(localStorage['redux-store']) :
        stateData
)

export default storeFactory

factory 被呼叫時會建構並回傳使用 logger 與 saver 的 store。

# Figma

[UI/UX Intro](https://www.youtube.com/watch?v=slzEfUjuhsQ)
[Auto Layout](https://www.youtube.com/watch?v=JR4N7cSJ54g)
[]
