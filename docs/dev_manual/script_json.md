## 1 api-script.json
!!! ms-abstract "api-script.json 示例"
    ```json
    {
        "id": "api",
        "name": "TCP插件脚本",
        "scriptType": "FromCreate",
        "options": {
            "form": {
                "labelAlign": "right",
                "layout": "vertical",
                "autoLabelWidth": true,
                "size": "small",
                "hideRequiredAsterisk": false,
                "showMessage": true,
                "inlineMessage": false,
                "scrollToFirstError": true
            },
            "submitBtn": false,
            "resetBtn": false
        },
        "apiDefinitionFields": [
            "content",
            "comments",
            "connTimeout",
            "resTimeout"
        ],
        "apiDebugFields": [
            "comments",
            "serverIp",
            "connTimeout",
            "port",
            "resTimeout",
            "soLinger",
            "eolByte",
            "closeConnection",
            "reUseConnection",
            "noDelay",
            "content",
            "classname",
            "username",
            "password"
        ],
        "script": [
            {
                "type": "select",
                "field": "classname",
                "title": "TCPClient",
                "info": "",
                "effect": {
                    "fetch": ""
                },
                "options": [
                    {
                        "value": "TCPClientImpl",
                        "label": "TCPClientImpl"
                    },
                    {
                        "value": "BinaryTCPClientImpl",
                        "label": "BinaryTCPClientImpl"
                    },
                    {
                        "value": "LengthPrefixedBinaryTCPClientImpl",
                        "label": "LengthPrefixedBinaryTCPClientImpl"
                    }
                ],
                "_fc_drag_tag": "select",
                "hidden": false,
                "display": true,
                "$required": "",
                "value": "TCPClientImpl"
            },
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 12
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "serverIp",
                                "title": "服务器名或 IP",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true,
                                "$required": ""
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 11,
                            "offset": 1
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "port",
                                "title": "端口",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true,
                                "$required": ""
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            },
            {
                "type": "input",
                "field": "content",
                "title": "发送内容",
                "info": "",
                "props": {
                    "type": "textarea"
                },
                "_fc_drag_tag": "input",
                "hidden": false,
                "display": true
            },
            {
                "type": "input",
                "field": "comments",
                "title": "描述",
                "info": "",
                "_fc_drag_tag": "input",
                "hidden": false,
                "display": true
            },
            {
                "type": "a-divider",
                "props": {
                    "orientation": "left"
                },
                "wrap": {
                    "show": false
                },
                "native": false,
                "children": [
                    "其他配置"
                ],
                "_fc_drag_tag": "a-divider",
                "hidden": false,
                "display": true
            },
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 12,
                            "push": 0,
                            "offset": 0
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "connTimeout",
                                "title": "链接超时(ms)",
                                "info": "",
                                "props": {
                                    "type": "number",
                                    "showWordLimit": false,
                                    "placeholder": "5000"
                                },
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true,
                                "$required": "",
                                "value": "5000"
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 11,
                            "offset": 1
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "resTimeout",
                                "title": "响应超时(ms)",
                                "info": "",
                                "props": {
                                    "type": "number",
                                    "showWordLimit": false,
                                    "placeholder": "5000"
                                },
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true,
                                "$required": "",
                                "value": "5000"
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            },
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 12
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "username",
                                "title": "用户名",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 11,
                            "offset": 1
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "password",
                                "title": "密码",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true,
                                "props": {
                                    "type": "password"
                                }
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            },
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 12
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "soLinger",
                                "title": "SO LINGER",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 11,
                            "offset": 1
                        },
                        "children": [
                            {
                                "type": "input",
                                "field": "eolByte",
                                "title": "行尾(EOL)字节值",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            },
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 8
                        },
                        "children": [
                            {
                                "type": "checkbox",
                                "field": "closeConnection",
                                "title": "关闭链接",
                                "info": "",
                                "effect": {
                                    "fetch": ""
                                },
                                "options": [
                                    {
                                        "label": "",
                                        "value": ""
                                    }
                                ],
                                "_fc_drag_tag": "checkbox",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 8
                        },
                        "children": [
                            {
                                "type": "checkbox",
                                "field": "reUseConnection",
                                "title": "Re-use connection",
                                "info": "",
                                "effect": {
                                    "fetch": ""
                                },
                                "options": [
                                    {
                                        "label": "",
                                        "value": ""
                                    }
                                ],
                                "_fc_drag_tag": "checkbox",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 8
                        },
                        "children": [
                            {
                                "type": "checkbox",
                                "field": "noDelay",
                                "title": "设置无延迟",
                                "info": "",
                                "effect": {
                                    "fetch": ""
                                },
                                "options": [
                                    {
                                        "label": "",
                                        "value": ""
                                    }
                                ],
                                "_fc_drag_tag": "checkbox",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            }
        ]
    }
    ```

## 2 env-script.json
!!! ms-abstract "env-script.json 示例"
    ```json
    {
        "id": "environment",
        "name": "TCP环境脚本",
        "tabName": "TCP配置",
        "scriptType": "FromCreate",
        "options": {
            "form": {
                "labelAlign": "right",
                "layout": "vertical",
                "autoLabelWidth": true,
                "size": "small",
                "hideRequiredAsterisk": false,
                "showMessage": true,
                "inlineMessage": false,
                "scrollToFirstError": true
            },
            "submitBtn": false,
            "resetBtn": false
        },
        "fields": [
            "serverIp",
            "port",
            "connTimeout",
            "resTimeout",
            "soLinger",
            "eolByte",
            "closeConnection",
            "reUseConnection",
            "noDelay",
            "classname",
            "username",
            "password"
        ],
        "script": [
            {
                "type": "FcRow",
                "children": [
                    {
                        "type": "col",
                        "props": {
                            "span": 20
                        },
                        "children": [
                            {
                                "type": "select",
                                "field": "classname",
                                "title": "TCPClient",
                                "info": "",
                                "effect": {
                                    "fetch": ""
                                },
                                "options": [
                                    {
                                        "value": "TCPClientImpl",
                                        "label": "TCPClientImpl"
                                    },
                                    {
                                        "value": "BinaryTCPClientImpl",
                                        "label": "BinaryTCPClientImpl"
                                    },
                                    {
                                        "value": "LengthPrefixedBinaryTCPClientImpl",
                                        "label": "LengthPrefixedBinaryTCPClientImpl"
                                    }
                                ],
                                "_fc_drag_tag": "select",
                                "hidden": false,
                                "display": true,
                                "$required": false
                            },
                            {
                                "type": "input",
                                "field": "serverIp",
                                "title": "服务器名或 IP",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "input",
                                "field": "port",
                                "title": "端口",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "input",
                                "field": "username",
                                "title": "用户名",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "input",
                                "field": "password",
                                "title": "密码",
                                "info": "",
                                "props": {
                                    "type": "password"
                                },
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "input",
                                "field": "soLinger",
                                "title": "SO LINGER",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "input",
                                "field": "eolByte",
                                "title": "行尾(EOL)字节值",
                                "info": "",
                                "_fc_drag_tag": "input",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "FcRow",
                                "children": [
                                    {
                                        "type": "col",
                                        "props": {
                                            "span": 12
                                        },
                                        "children": [
                                            {
                                                "type": "input",
                                                "field": "connTimeout",
                                                "title": "链接超时(ms)",
                                                "info": "",
                                                "props": {
                                                    "type": "number",
                                                    "showWordLimit": false,
                                                    "placeholder": "5000"
                                                },
                                                "_fc_drag_tag": "input",
                                                "hidden": false,
                                                "display": true,
                                                "value": "5000"
                                            }
                                        ],
                                        "_fc_drag_tag": "col",
                                        "hidden": false,
                                        "display": true
                                    },
                                    {
                                        "type": "col",
                                        "props": {
                                            "span": 11,
                                            "offset": 1
                                        },
                                        "children": [
                                            {
                                                "type": "input",
                                                "field": "resTimeout",
                                                "title": "响应超时(ms)",
                                                "info": "",
                                                "props": {
                                                    "type": "number",
                                                    "showWordLimit": false,
                                                    "placeholder": "5000"
                                                },
                                                "_fc_drag_tag": "input",
                                                "hidden": false,
                                                "display": true,
                                                "value": "5000"
                                            }
                                        ],
                                        "_fc_drag_tag": "col",
                                        "hidden": false,
                                        "display": true
                                    }
                                ],
                                "_fc_drag_tag": "row",
                                "hidden": false,
                                "display": true
                            },
                            {
                                "type": "FcRow",
                                "children": [
                                    {
                                        "type": "col",
                                        "props": {
                                            "span": 8
                                        },
                                        "children": [
                                            {
                                                "type": "checkbox",
                                                "field": "closeConnection",
                                                "title": "关闭链接",
                                                "info": "",
                                                "effect": {
                                                    "fetch": ""
                                                },
                                                "options": [
                                                    {
                                                        "label": "",
                                                        "value": ""
                                                    }
                                                ],
                                                "_fc_drag_tag": "checkbox",
                                                "hidden": false,
                                                "display": true
                                            }
                                        ],
                                        "_fc_drag_tag": "col",
                                        "hidden": false,
                                        "display": true
                                    },
                                    {
                                        "type": "col",
                                        "props": {
                                            "span": 8
                                        },
                                        "children": [
                                            {
                                                "type": "checkbox",
                                                "field": "reUseConnection",
                                                "title": "Re-use connection",
                                                "info": "",
                                                "effect": {
                                                    "fetch": ""
                                                },
                                                "options": [
                                                    {
                                                        "label": "",
                                                        "value": ""
                                                    }
                                                ],
                                                "_fc_drag_tag": "checkbox",
                                                "hidden": false,
                                                "display": true
                                            }
                                        ],
                                        "_fc_drag_tag": "col",
                                        "hidden": false,
                                        "display": true
                                    },
                                    {
                                        "type": "col",
                                        "props": {
                                            "span": 8
                                        },
                                        "children": [
                                            {
                                                "type": "checkbox",
                                                "field": "noDelay",
                                                "title": "设置无延迟",
                                                "info": "",
                                                "effect": {
                                                    "fetch": ""
                                                },
                                                "options": [
                                                    {
                                                        "label": "",
                                                        "value": ""
                                                    }
                                                ],
                                                "_fc_drag_tag": "checkbox",
                                                "hidden": false,
                                                "display": true
                                            }
                                        ],
                                        "_fc_drag_tag": "col",
                                        "hidden": false,
                                        "display": true
                                    }
                                ],
                                "_fc_drag_tag": "row",
                                "hidden": false,
                                "display": true
                            }
                        ],
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    },
                    {
                        "type": "col",
                        "props": {
                            "span": 4
                        },
                        "_fc_drag_tag": "col",
                        "hidden": false,
                        "display": true
                    }
                ],
                "_fc_drag_tag": "row",
                "hidden": false,
                "display": true
            }
        ]
    }
    ```