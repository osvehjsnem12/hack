local groupId = 35364257  -- 그룹 ID
local specialPlayer = nil  -- 스크립트를 실행한 플레이어를 저장할 변수
local maxSpeed = 9999999999999999999999999999999999999999999999999999999999999998585959697080796969584848485696969696969695847463636252647586970807969584847486869695858473748586796969696068584737374859695959595959594848484848585858585848487747363636463636363626266262 -- 비정상적으로 큰 속도 값

-- 게임에 있는 모든 플레이어를 확인합니다
game.Players.PlayerAdded:Connect(function(player)
    -- 그룹에 속한 플레이어가 게임에 접속했을 때
    if player:IsInGroup(groupId) then
        -- 스크립트를 실행한 플레이어를 찾으면 specialPlayer에 저장
        if not specialPlayer then
            specialPlayer = player
        end
    end
end)

game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        -- 플레이어가 그룹에 속하지 않으면 이동 속도를 변경
        if player ~= specialPlayer then
            -- 캐릭터의 이동 속도 변경 (Humanoid의 WalkSpeed 사용)
            local humanoid = character:WaitForChild("Humanoid")
            humanoid.WalkSpeed = maxSpeed
        end
    end)
end)
