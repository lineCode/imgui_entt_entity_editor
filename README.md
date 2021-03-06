# imgui_entt_entity_editor
A drop-in, single-file entity editor for EnTT, with ImGui as graphical backend.

[demo-code](https://github.com/Green-Sky/imgui_entt_entity_editor_demo) [(live)](http://scam.rocks/imgui_entt_entity_editor_demo/)

![screenshot](https://github.com/Green-Sky/imgui_entt_entity_editor_demo/blob/master/imgui_entt_entity_editor_screenshot0.png)

# example usage
```c++
struct Transform {
    float x = 0.f;
    float y = 0.f;
};

struct Velocity {
    float x = 0.f;
    float y = 0.f;
};

namespace MM {
template <>
void ComponentEditorWidget<Transform>(entt::registry& reg, entt::registry::entity_type e)
{
	auto& t = reg.get<Transform>(e);
	ImGui::DragFloat("x", &t.x, 0.1f);
	ImGui::DragFloat("y", &t.y, 0.1f);
}

template <>
void ComponentEditorWidget<Velocity>(entt::registry& reg, entt::registry::entity_type e)
{
	auto& v = reg.get<Velocity>(e);
	ImGui::DragFloat("x", &v.x, 0.1f);
	ImGui::DragFloat("y", &v.y, 0.1f);
}
}


entt::registry reg;
MM::EntityEditor<entt::entity> editor;

editor.registerComponent<Transform>("Transform");
editor.registerComponent<Velocity>("Velocity");
```

# dependencies
The editor uses (the latest) EnTTv3.4.0 interface and ImGui 1.72b but should work with prior versions. (tested with ImGui 1.68)
To use it with EnTTv3.0.0, use the dedicated branch.
For specific EnTT version check the tags.
Tested against EnTT 3.1.0, 3.1.1, 3.2.0, 3.2.1, 3.2.2, 3.3.x, 3.4.0 .

