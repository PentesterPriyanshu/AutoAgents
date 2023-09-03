# AutoAgents: A Framework for Automatic Agent Generation

<p align="center">
<a href=""><img src="docs/resources/logo-autoagents.jpg" alt="autoagents logo: A Framework for Automatic Agent Generation." width="150px"></a>
</p>

<p align="center">
<b>Generate different roles for GPTs to form a collaborative entity for complex tasks.</b>
</p>

<p align="center">
<a href="docs/README_CN.md"><img src="https://img.shields.io/badge/文档-中文版-blue.svg" alt="CN doc"></a>
<a href="README.md"><img src="https://img.shields.io/badge/document-English-blue.svg" alt="EN doc"></a>
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
</p>

AutoAgents is an experimental open-source application for An Automatic Agents Generation Experiment based on LLM. This program, driven by LLM, autonomously generates multi-agents to achieve whatever goal you set.

<p align="center">
    <img src=./docs/resources/framework2.jpg width="800">
</p>

## <a name="updates"/> :boom: Updates
- **2023.08.30**: Adding a custom agent collection, AgentBank, allows you to add custom agents. 

## 🚀 Features
- **Planner**: Determines the expert roles to be added and the specific execution plan according to the problem.
- **Tools**: The set of tools that can be used, currently only compatible with the search tools.
- **Observers**: Responsible for reflecting on whether the planner and the results in the execution process are reasonable, currently including reflection checks on Agents, Plan, and Action.
- **Agents**: Expert role agents generated by the planner, including name, expertise, tools used, and LLM enhancement.
- **Plan**: The execution plan is composed of the generated expert roles, each step of the execution plan has at least one expert role agent.
- **Actions**: The specific actions of the expert roles in the execution plan, such as calling tools or outputting results.

## Demo
Online demo: 
- [Demo / HuggingFace Spaces](https://huggingface.co/spaces/LinkSoul/AutoAgents)

Video demo:
- **Rumor Verification**
<video src='https://github.com/shiyemin/AutoAgents/assets/1501158/41898e0d-4137-450c-ad9b-bfb9b8c1d27b.mp4'></video>
- **Gluttonous Snake**
<video src='https://github.com/shiyemin/AutoAgents/assets/1501158/97e408cb-b70d-4045-82ea-07319c085138.mp4'></video>

## Installation and Usage

### Installation

```bash
git clone https://github.com/LinkSoul-AI/AutoAgents
cd AutoAgents
python setup.py install
```

### Configuration

- Configure your `OPENAI_API_KEY` in any of `config/key.yaml / config/config.yaml / env`
- Priority order: `config/key.yaml > config/config.yaml > env`

```bash
# Copy the configuration file and make the necessary modifications.
cp config/config.yaml config/key.yaml
```

| Variable Name                              | config/key.yaml                           | env                                             |
| ------------------------------------------ | ----------------------------------------- | ----------------------------------------------- |
| OPENAI_API_KEY # Replace with your own key | OPENAI_API_KEY: "sk-..."                  | export OPENAI_API_KEY="sk-..."                  |
| OPENAI_API_BASE # Optional                 | OPENAI_API_BASE: "https://<YOUR_SITE>/v1" | export OPENAI_API_BASE="https://<YOUR_SITE>/v1" |

### Usage
- Commandline mode:
```python
python main.py --mode commandline --llm_api_key YOUR_OPENAI_API_KEY --serapi_key YOUR_SERPAPI_KEY --idea "Is LK-99 really a room temperature superconducting material?"
```
- Websocket service mode:
```python
python main.py --mode service --host "127.0.0.1" --port 9000
```

### Docker
- Build docker image:
```bash
IMAGE="linksoul.ai/autoagents"
VERSION=1.0

docker build -f docker/Dockerfile -t "${IMAGE}:${VERSION}" .
```
- Start docker container:
```bash
docker run -it --rm -p 7860:7860 "${IMAGE}:${VERSION}"
```
- Open http://127.0.0.1:7860 in the browser.

## Contact Information

If you have any questions or feedback about this project, please feel free to contact us. We highly appreciate your suggestions!

- **Email:** gy.chen@foxmail.com, ymshi@linksoul.ai
- **GitHub Issues:** For more technical inquiries, you can also create a new issue in our [GitHub repository](https://github.com/LinkSoul-AI/AutoAgents/issues).

We will respond to all questions within 2-3 business days.

## License

[Apache-2.0 license](https://raw.githubusercontent.com/LinkSoul-AI/AutoAgents/main/LICENSE)

## Citation

If you find our work and this repository useful, please consider giving a star :star: and citation :beer::
```bibtex
@article{chen2023auto,
  title={AutoAgents: The Automatic Agents Generation Framework},
  author={Chen, Guangyao and Dong, Siwei and Shu, Yu and Zhang, Ge and Jaward, Sesay and Börje, Karlsson and Fu, Jie and Shi, Yemin},
  journal={arXiv preprint},
  year={2023}
}
```

## Wechat Group

<img src=".github/QRcode.jpg" alt="Wechat Group" width="200"/>

## Acknowledgements
The [system](https://github.com/LinkSoul-AI/AutoAgents/tree/main/autoagents/system), [action_banck](https://github.com/LinkSoul-AI/AutoAgents/tree/main/autoagents/actions/action_bank) and [role_bank](https://github.com/LinkSoul-AI/AutoAgents/tree/main/autoagents/roles/role_bank) of this code base is built using [MetaGPT](https://github.com/geekan/MetaGPT)
